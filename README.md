# 2024 Advent of Code (in Alan)

This is my first time participating in the Advent of Code. My goal is not to make it onto any leaderboard or have the cleverest solution. It's to use these problems as a way to identify gaps in the Alan programming language and plug them.

The folder structure will be `day<N>/prob<M>` for each problem of each day. Within this folder will be another `README.md` that will include:

1. The commit SHA of the exact version of [Alan](https://github.com/alantech/alan) used to compile the program and successfully get the correct output for both native and JS.
2. A listing of PRs (with short descriptions) that were necessary to implement the code in question.
3. If it was possible, a description of an alternative implementation I felt was possible without modifying Alan, but that I decided against because the code was "non-obvious" or effectively implementing a feature that should be in the language or standard library.
4. Instructions on how to build the native and JS programs. This will *usually* be `alan compile source.ln` and `alan bundle source.ln` within the problem directory, but it may be something else. (I might also just use `alan test source.ln` and `alan test --js source.ln` and have it output the results directly, but there can be no CLI arguments to such programs).

The source code itself will have comments explaining what is being done and why. Because Github doesn't have a syntax highlighter for Alan (for obvious reasons), I will also include a screenshot of the code highlighted [in Vim](https://github.com/alantech/vim-alan) to improve readability for anyone coming across this repo.
