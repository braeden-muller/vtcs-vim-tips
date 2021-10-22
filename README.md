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
5. `j` and `k` move up and down lines separated by newline, skipping any sort of
    overflow created from having lines be too long, even though they're visually
    below the line you're currently on. If you wish to move up and down visual
    lines on the screen instead of lines separated by newline, use `gj` and
    `gk.` This is useful if you’re using Vim to type up an essay with paragraphs
    that will likely overflow!

    - Example: If your cursor is where the underline is next to *Duis*, pressing
    `j` will make it go to the *p* in *proident* since that is where the formal
    new line is, but pressing `gj` will make it go down to the *e* in *dolore*:
    ```
    2   Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusm
          tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
    1   veniam, quis nostrud exercitation ullamco laboris aliquip ex e
    96  commodo consequat. Duis_ ute irure dolor in reprehenderit in voluptate
          velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
    1   occaecat cupidatat non proident, sunt in culpa qui officia deserunt mo
          llit anim id est laborum.
    ```
6. In addition to being able to yank and paste text, you can yank/paste text to
    one of 26 registers denoted by each of the lowercase letters so you can have
    several texts saved at once. These registers can be triggered via
    “<lowercase letter>
    - Example: `"ryw` yanks a word and puts it in the `r` register
    `"rp` pastes the word saved into the `r` register
7. Need to delete something in parenthesis? Just go inside that pair of
    parenthesis and type `di(` [delete inside parenthesis]. You can replace `i`
    with `a` (around) to delete the parenthesis as well. This works with
    brackets, curly braces and anything else similar to that.
8. Need to repeat a series of motions several times? Create a macro using
    `q[a-z]` and then recording that series of motions and stopping it by
    pressing `q` again. Afterwards this macro can be called by `@[a-z]`
    - Example: `qa/(<Enter>di($pq` Creates a macro to find parenthesis and
        delete and paste it’s contents at the end of the line `@a` calls the
        macro to delete in parenthesis and paste at the end of the line
        `10@a` calls the macro 10 times, pasting the contents of the first `()`
        at the end of the line and then finding the next `(` and repeating the
        process.
9. Words in vim are separated by spaces, minuses, punctuation some other general
    symbols. If you want to refer to a word in the sense that it’s only
    separated by spaces, use uppercase `W`.
    - Example: `dw` at the start of the line `test-big-word` with more words
        after will delete `test`. `dW` at the start of the same line will delete
        `test-big-word`.
10. Pressing `Shift+K` while hovering over a word will look up that word's
    `man` page.
11. Pressing `;` and `,` after typing `f/t` will bring you to the next/previous
    match of your target key.
12. If you find yourself repeating a series of keys often you might want to
    consider mapping that set of keys to a keystroke in your `vimrc`. Map
    something by typing `map <keystroke> <combo of keys it represents>` to make
    a `map` that works for normal and visual mode. It is recommended to add a
    `key n (normal)`, `i (insert)`, `v (visual)`, etc. in front of the word
    `map` to make it specific to a mode. It is also recommended to change it to
    `noremap` which will prevent remapped keys from interfering with other
    remapped keys.
    - Example:  `nnoremap j gj` will make it so the `j` key moves down 1 visual
    line instead of 1 actual line.
