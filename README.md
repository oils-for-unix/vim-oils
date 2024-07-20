Vim Syntax Highlighting for YSH
====

Right now we're doing YSH only, not OSH.

Here's an alternative plugin supports more features:

- <https://github.com/sj2tpgk/vim-oil>

Though I found an issue where it incorrectly highlighted single quotes within
`#` comments.

So I am trying something simpler.

## Notes

- The (nascent) "micro syntax" style supports only
  - comments
  - string literals

But maybe that is too minimal.  I also like to highlight:

- `\n` within string literals (and outside perhaps)
- Within double quoted string literals:
  - `$myvar`
  - `${myvar}`
  - `$[myvar]`

### Command vs. Expression Mode

Users do have problems with this distinction.

I wonder if syntax highlighting can help.  Here are the places it changes in YSH

    var y = 42 + f(expr)
    var y = ^[42 + f(expr)]
    # const, setvar, setglobal

    = 42 + f(expr)
    call f(expr)

    echo $[42 + f(expr)]
    echo @[42 + f(expr)]

    pp (42 + expr)
    pp [42 + expr]

We also have:

    proc p (; x, y) { ...

    func f (x, y) { ...

