## VTCS Vim Tips
*The collected works of Lizard Wizard#6976 (Jus Jus #2492)*
1. Use `i` to insert text before the cursor and `a` to insert text after it.
    Switching these letters to uppercase (`Shift + i` and `Shift + a`) will
    allow you to insert text at the start and end of the line your cursor is on
    (start of the line being the first non-whitespace character).
2. Putting `set nu rnu` (number, relative line number) in your `.vimrc` will
    keep the line number your cursor is on while switching all the other lines
    to be how many line numbers away from your current line it is. This is
    useful with the `j` and `k` keys since you can see how many lines up/down
    you have to go (alternatively you can have set `nu` for regular numbers or
    set `rnu` for relative numbers with a `0` instead of your current line
    number).
    - Example: *You are on line `96`:*
    ```
    3   Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
    2   tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
    1   veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
    96  commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
    1   velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
    2   occaecat cupidatat non proident, sunt in culpa qui officia deserunt
    3   mollit anim id est laborum.
    ```
3. When initially learning Vim, stop using (disable if you must) `←, ↓, ↑, →` to
    get used to `h, j, k, l`. Afterwards, avoid using `h, j, k, l` to move
    around and instead use more efficient methods such move using text movements
    (`w, e, b, (, {, etc.`) or the powerful search commands (`f, t, /, ?`).
4. Map your `caps lock` to `esc` (this must be done outside Vim), it will make
    it easier to leave insert mode since your hand won’t have to leave the home
    row.
