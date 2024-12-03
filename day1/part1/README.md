# Day 1 Part 1

## Implemented with [this Alan commit](https://github.com/alantech/alan/commit/e17a201a9a261780a36143b174c14310db837308)

## Required PRs

1. [Branch support for Cargo git deps](https://github.com/alantech/alan/pull/982) - A dev accelerator that I had been putting off after monorepo changes that was easier than I anticipated
2. [Implement the `sort` functions](https://github.com/alantech/alan/pull/986) - Adding `sort` functions for the `Array` and `Buffer` types that both accepts a sorting function that returns an `i8` and without a sorting function assuming smallest-to-greatest and implemented assuming `eq` and `lt` exists for the provided type.
3. [Implement the bare minimum for `@std/fs`: file reading support](https://github.com/alantech/alan/pull/987) - As described, a very minimal standard library implementation with only a `File` type and a `string` function to read a text file into a string.
4. [Fix calling `reduce` in Javascript when the default value is a tuple](https://github.com/alantech/alan/pull/988) - A bug in the type resolution found for the Javascript bindings. This PR works around that bug while making the generated code slightly cleaner, but doesn't fix the root cause (which is some sort of type equality bug).

## Build and run commands

* Native: `alan test source.ln`
* Javascript: `alan test --js source.ln`

## Thoughts

There are a few QoL things that I ran into during this problem that I want to fix/tackle, most of them added as comments to the source code, but not all of them.

* I ran into a bug where a filter function that I wanted to write couldn't be written, because the automatically-derived type functions didn't exist when they should have. I have run into this a few times before and it's a pretty bad compiler bug that I should tackle before pushing for more general purpose usage. (I wanted to write `.filter(fn (n: i64!) = n.i64.exists)` but it said that a function with the call signature `i64(i64!)` doesn't exist, which shouldn't be happening. I left a comment that what I really want in this place is a `success{T}(T!) -> bool` function, but the other representation shouldn't have failed me.
* I ran into an unexpected behavior of string parsing in Javascript where a string with **no numeric characters** parses to `0`. I noticed `parseInt` returns `NaN` in that case, but you can't directly use `parseInt` for 64-bit integers, so I'll probably have to write my own parsing function wrappers for JS to work around this nonsense.
* I really wanted a `zip` function for the last part to be more legible, but the `map` I used was acceptable.
