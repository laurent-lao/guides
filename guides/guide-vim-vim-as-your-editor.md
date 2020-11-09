# VIM as your editor

The following page are notes taken regarding the Youtube playlist [Vim As Your Editor](https://www.youtube.com/watch?v=H3o4l4GVLW0&list=PLm323Lc7iSW_wuxqmKx_xxNtJC_hJbQ7R) by ThePrimeagen.

## Vim As Your Editor (1/6): The Basic Vim Movements

### Fundamental navigation keys

* `H`, `L` to move left and right (respectively)
* `J`, `K` to move up and down (respectively)
* `W`, `B` to move forward and backwards by an entire word (respectively)

### Fundamental editing commands

* `YY` to copy a line, then either:
    * `P` to paste that line, or
    * `DD` to save the current line to the register and then delete that whole line
* `U` to undo that command
* You can do combinations prefaced by `Y` or `D` and then one of the fundamental navigation keys, e.g:
    * `YW` to copy the next word (`DW` to delete the next word)
    * `YL` to copy the next character (`DL` to delete the next character)

### VIM modes

#### Visual Mode
* `Shift+V` to highlight a line, then `J` or `K` to highlight upwards to downwards, then either:
    * `Y` to copy the hightlighted block, or
    * `D` to delete the highlighted block
        * While `D` deletes the highlighted block, the block is saved into a register. You can use `D` and then `P` to move a whole function, for example.
* `V` (lowercase) to start hightlight at the current cursor location, then:
    * Combine with the navigation keys like `W` or `L` to highlight a whole word or the next character

#### Insert Mode
* `I` goes to insert mode (to type directly like any text editor)
    * You can leave insert mode by either:
        * Pressing `ESC` or,
        * Pressing `Ctrl+C` or,
        * Pressing `Ctrl+[`

#### Column commands
* `:w` to save the file
* `:q` to quit, or
    * `:wq` to save and quit
    * `:!q` to force quit without saving anything

