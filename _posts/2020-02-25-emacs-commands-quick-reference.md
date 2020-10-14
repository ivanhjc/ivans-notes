---
excerpt: "A collection of most commonly used Emacs commands"
last_modified_at: 2020-10-14
toc: true
categories:
  - productivity
tags:
  - emacs
---

# Commands

  - Key-bindings (or shortcuts) are represented with symbols specified
    in the [key notations](#key-notations) table.
  - Key-bindings that are not packed with Emacs or other packages are
    marked with an `*`.

## Key notations

| Symbol | Meaning                                                        |
| ------ | -------------------------------------------------------------- |
| C      | Ctrl key                                                       |
| M      | Meta/Alt key                                                   |
| S      | Shift key                                                      |
| \-     | Hyphen. Keys connected with hyphens should be pressed together |
|        | White space, indicating a short pause between key pressings    |
| RET    | Return/Enter key                                               |
| SPC    | Space key                                                      |
| DEL    | Backspace key                                                  |
| CMD    | Command                                                        |
| ,      | Comma, used to separate optional or closely-related commands   |
| A\|B    | Either A or B                                                  |
| \[A\]  | A is optional, i.e., it can be omitted or present              |
| …      | Repeat the last stroke indefinitely                            |

## Help

| Keys                | Meaning                                                                   | Command            |
| ------------------- | ------------------------------------------------------------------------- | ------------------ |
| C-h ?               | Show general help commands                                                | help-for-help      |
| C-h C-a             | Show welcome screen                                                       | about-emacs        |
| C-h t               | Open Emacs tutorial                                                       | help-with-tutorial |
| C-h i               | Open the info buffer                                                      | info               |
| C-h k               | Look up key                                                               | describe-key       |
| C-h f               | Look up command                                                           | describe-function  |
| C-h v               | Look up variable                                                          | describe-variable  |
| C-h P               | Describe package                                                          | describe-package   |
| C-h .               | Display tooltip in the echo area                                          | display-local-help |
| \<prefix\> {C-h\|F1} | Show the list of key-bindings starting with the prefix key, e.g. `C-x C-h` displays the list of key-bindings starting with `C-x`. |                    |

## Navigation

| Keys      | Meaning                                                     | Command                                                                            |
| --------- | ----------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| C-f       | Go forward a character                                      | forward-char                                                                       |
| C-b       | Go backward a character                                     | backward-char                                                                      |
| M-b       | Go to word start                                            | backward-word                                                                      |
| M-f       | Go to word end                                              | forward-word                                                                       |
| C-p       | Go to previous line                                         | previous-line                                                                      |
| C-n       | Go to next line                                             | next-line                                                                          |
| C-a       | Go to line start                                            | move-beginning-of-line                                                             |
| C-e       | Go to line end                                              | move-end-of-line                                                                   |
| M-a       | Go to sentence start                                        | backward-sentence                                                                  |
| M-e       | Go to sentence end                                          | forward-sentence                                                                   |
| M-}       | Go to next paragraph                                        | forward-paragraph                                                                  |
| M-{       | Go to previous paragraph                                    | backward-paragraph                                                                 |
| M-\]      | Go to next blank line separated block                       | xah-forward-block [*](#xah-forward-block)   |
| M-\[      | Go to previous blank line separated block                   | xah-backward-block [*](#xah-backward-block) |
| M-\<      | Go to buffer start                                          | beginning-of-buffer                                                                |
| M-\>      | Go to buffer end                                            | end-of-buffer                                                                      |
| M-r        | Go to buffer center, top, or bottom                          | move-to-window-line-top-bottom |
| C-M-f     | Go to the matched closing bracket                           | forward-sexp                                                                       |
| C-M-b     | Go to the matched opening bracket                           | forward-sexp                                                                       |
| C-M-e     | Go to next end of defun                                     | end-of-defun                                                                       |
| C-M-a     | Go to previous beginning of defun                           | beginning-of-defun                                                                 |
| C-x \<    | Scroll text in the current window to the left               | scroll-left                                                                        |
| C-x \>    | Scroll text in the current window to the right              | scroll-right                                                                       |
| C-v       | Scroll forward one screenful                                | scroll-up-command                                                                  |
| M-v       | Scroll backward one screenful                               | scroll-down-command                                                                |
| C-M-v     | Scroll other window forward one screenful                   | scroll-other-window                                                                |
| S-C-M-v   | Scroll other window backward one screenful                  | scroll-other-window-down                                                           |
| C-l       | Move the text around the cursor to the center of the screen | recenter-top-bottom                                                                |
| M-g g     | Go to line                                                  | goto-line                                                                          |
| M-g c     | Go to character                                             | goto-char                                                                          |
| C-u C-SPC | Go to last marked position in current buffer                | set-mark-command                                                                   |
| ???       | Go to next marked position in current buffer                |                                                                                    |
| C-x C-SPC | Go to last marked position in all buffers                   | set-mark-command                                                                   |
| ???       | Go to next marked position in all buffers                   |                                                                                    |
| ???       | Go to last edited position in current buffer                |                                                                                    |
| ???       | Go to next edited position in current buffer                |                                                                                    |
| ???       | Go to last edited position in all buffers                   |                                                                                    |
| ???       | Go to next edited position in all buffers                   |                                                                                    |

## Selection

| Keys    | Meaning                                                             | Command                |
| ------- | ------------------------------------------------------------------- | ---------------------- |
| C-x h   | Select all.                                                         | mark-whole-buffer      |
| C-S-p   | Up with selection.                                                  | previous-line          |
| C-S-n   | Down with selection.                                                | next-line              |
| C-S-f   | Forward with selection.                                             | forward-char           |
| C-S-b   | Backward with selection.                                            | backward-char          |
| M-S-f   | Forward with selection to word end.                                 | forward-word           |
| M-S-b   | Backward with selection to word start.                              | backward-word          |
| C-S-e   | Forward with selection to line end.                                 | move-end-of-line       |
| C-S-a   | Backward with selection to line start.                              | move-beginning-of-line |
| C-SPC   | Toggle sticky selection.                                            | set-mark-command       |
| C-x SPC | Toggle rectangle mark mode.                                         | rectangle-mark-mode    |
| M-=     | Show the number of lines, words, and characters in selected region. | count-words-region     |

## Editing

| Keys      | Meaning                                                                                                                    | Command                                                                                              |
| --------- | -------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| C-d       | Delete next character.                                                                                                     | delete-char                                                                                          |
| DEL       | Delete previous character.                                                                                                 | backward-delete-char-untabify                                                                        |
| ???       | Delete entire line.                                                                                                        |                                                                                                      |
| M-d       | Kill next word.                                                                                                            | kill-word                                                                                            |
| {M¦C}-DEL | Kill previous word.                                                                                                        | backward-kill-word                                                                                   |
| C-k       | Kill to line end. `M-0 ~` to kill to line start.                                                                           | kill-line                                                                                            |
| C-S-DEL   | Kill entire line.                                                                                                          | kill-whole-line                                                                                      |
| C-w       | Kill region.                                                                                                               | kill-region                                                                                          |
| M-w       | Copy region/rectangle                                                                                                      | kill-ring-save                                                                                       |
| C-y       | Yank/Paste last killed region/rectangle.                                                                                   | yank                                                                                                 |
| C-x r k   | Kill rectangle                                                                                                             | kill-rectangle                                                                                       |
| C-x r y   | Yank rectangle                                                                                                             | yank-rectangle                                                                                       |
| C-/       | Undo. `C-f ~` to redo.                                                                                                     | undo                                                                                                 |
| M-c       | Capitalize word.                                                                                                           | capitalize-word                                                                                      |
|           | Capitalize region.                                                                                                         | capitalize-region                                                                                    |
| M-u       | Turn all letters of next word uppercase.                                                                                   | upcase-word                                                                                          |
| M-l       | Turn all letters of next word lowercase                                                                                    | downcase-word                                                                                        |
| C-x C-u   | Turn all letters of selected region uppercase.                                                                             | upcase-region                                                                                        |
| C-x C-l   | Turn all letters of selected region lowercase.                                                                             | downcase-region                                                                                      |
| C-g       | Quit a command.                                                                                                            | keyboard-quit                                                                                        |
| C-o       | Insert a new line and leave the cursor unmoved.                                                                            | open-line                                                                                            |
| M-\\      | Delete all spaces and tabs around cursor.                                                                                  | delete-horizontal-space                                                                              |
| C-x C-o   | Delete blank lines surrounding the cursor.                                                                                 | delete-blank-lines                                                                                   |
| ???       | Toggle camelcase-aware editing for current buffer.                                                                         |                                                                                                      |
| S-RET     | Open line below without breaking current line.                                                                             | newline-below-without-break ([*](#newline-below-without-break)) |
| C-S-RET   | Open line above without breaking current line.                                                                             | newline-above-without-break ([*](#newline-above-without-break)) |
| TAB       | Indent current line. Use `C-u <n> C-x Tab` to indent the selected region n columns. Use negative number for n to unindent. | indent-for-tab-command                                                                               |
| C-q       | Read next input character and insert it. This is useful for inserting control characters.                                  | quoted-insert                                                                                        |
| C-x =     | Describe character at point. `C-u ~` to show more details.                                                                 | what-cursor-position                                                                                 |

## Searching

| Keys | Meaning                       | Command          |
| ---- | ----------------------------- | ---------------- |
| C-s  | Incremental search forward.   | isearch-forward  |
| C-r  | Incremental finding backward. | isearch-backward |
| M-%  | Query and replace.            | query-replace    |

## Buffers, windows and frames

| Keys          | Meaning                                                                                                                                                                                                          | Command                        |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| C-x b         | Switch to buffer in current window. Create new buffer if the given buffer name doesn’t exist.                                                                                                                    | switch-to-buffer               |
| C-x 4 b       | Switch to buffer in another window.                                                                                                                                                                              | switch-to-buffer-other-window  |
| C-x 4 C-o     | Display buffer in another window.                                                                                                                                                                                | display-buffer                 |
| C-x 5 b       | Switch to buffer in another frame.                                                                                                                                                                               | switch-to-buffer-other-frame   |
| C-x \<left\>  | Switch to previous buffer.                                                                                                                                                                                       | previous-buffer                |
| C-x \<right\> | Switch to next buffer                                                                                                                                                                                            | next-buffer                    |
| C-x C-b       | List buffers                                                                                                                                                                                                     | list-buffers                   |
| M-n           | Go to next window                                                                                                                                                                                                | other-window                   |
| M-p           | Go to previous window                                                                                                                                                                                            | prev-window                    |
| C-x k         | Kill buffer                                                                                                                                                                                                      | kill-buffer                    |
| C-x C-s       | Save buffer                                                                                                                                                                                                      | save-buffer                    |
| C-x s         | Save some modified file-visiting buffers.                                                                                                                                                                        | save-some-buffers              |
| C-x 0         | Close current window.                                                                                                                                                                                            | delete-window                  |
| C-x 1         | Go back to one-window editing.                                                                                                                                                                                   | delete-other-windows           |
| C-x 2         | Split window below. `C-u <n> ~` to specify height.                                                                                                                                                               | split-window-below             |
| C-x 3         | Split window right. `C-u <n> ~` to specify width.                                                                                                                                                                | split-window-right             |
| S-\<arrow\>\* | Switch directionally between windows. By default it's not enabled. Type \`M-x windmove-default-keybingds\` to enable it or add \`(windmove-default-keybindings)\` to init file to enable it for future sessions. | windmove-\*                    |
| C-x C-c       | Kill all buffers and exit emacs.                                                                                                                                                                                 | save-buffers-kill-terminal     |
|               | Open shell. `C-u M-x ~` to open another running shell.                                                                                                                                                           | shell                          |
|               | Open Emacs shell.                                                                                                                                                                                                | eshell                         |
| C-c C-l       | Display a list of recent inputs entered into the current buffer.                                                                                                                                                 | comint-dynamic-list-input-ring |
| C-x m         | Open mail buffer.                                                                                                                                                                                                | compose-mail                   |
| C-x C-=       | Adjust font size.                                                                                                                                                                                                | text-scale-adjust              |
|               | Truncate long lines or wrap them.                                                                                                                                                                                | toggle-word-wrap               |
| C-z           | Suspend emacs. In shell type `%emacs` to resume.                                                                                                                                                                 | suspend-frame                  |

## Files and directories

| Keys    | Meaning                                                                     | Command                |
| ------- | --------------------------------------------------------------------------- | ---------------------- |
| C-x C-f | Open or create a file in current window                                     | find-file              |
| C-x 4 f | Open or create a file in another window                                     | find-file-other-window |
| M-F2    | Open file in browser. `(global-set-key (kbd "<M-f2>") 'browse-url-of-file)` | browse-url-of-file     |
| C-x C-d | Display a brief directory listing. `C-u ~` to display verbosely.            | list-directory         |
|         |                                                                             |                        |

### Dired mode

| Keys    | Meaning                             | Command            |
| ------- | ----------------------------------- | ------------------ |
| C-x d   | Enter dired mode in current window. | dired              |
| C-x 4 d | Enter dired mode in another window. | dired-other-window |

When in dired more:

| Keys | Meaning                      | Command                  |
| ---- | ---------------------------- | ------------------------ |
| d    | Flag files for deletion.     | dired-flag-file-deletion |
| D    | Delete file on current line. | dired-do-delete          |
| x    | Delete flaged files.         | dired-do-flagged-delete  |
| g    | Refresh the mode buffer.     | revert-buffer            |

### Diff mode

| Keys | Meaning                                                                        | Command               |
| ---- | ------------------------------------------------------------------------------ | --------------------- |
|      | Enter diff mode in current window which compares two files                     | diff                  |
|      | Enter diff mode in current window which compares current buffer with its file. | diff-buffer-with-file |

When in diff mode:

| Keys | Meaning                 | Command |
| ---- | ----------------------- | ------- |
| g    | Refresh the mode buffer |         |

## Meta commands
Commands on commands

| Keys                    | Meaning                                                      | Command                  |
| ----------------------- | ------------------------------------------------------------ | ------------------------ |
| {M-\<n\>¦C-u \<n\>} CMD | Run a command n times. See `C-h i (emacs)Arguments`.         | digit-argument           |
| M-x                     | Run a command.                                               | execute-extended-command |
| M-\!                    | Run a shell command.                                         | shell-command            |
| C-x z                   | Run last command. Press z continuously to repeat more times. | repeat                   |
| M-:                     | Evaluate EXP and print value in the echo area.               | eval-expression          |
| C-x C-e                 | Evaluate sexp before point; print value in the echo area.    | eval-last-sexp           |
| C-j                     | Evaluate sexp before point; print value into current buffer. | eval-print-last-sexp     |

## Org mode

### Headings and subtrees

| Keys          | Meaning                                                                        | Command                                 |
| ------------- | ------------------------------------------------------------------------------ | --------------------------------------- |
| TAB           | Expand/Collapse outline entry, or indent plain list item                       | org-cycle                               |
| S-TAB         | Cycle visibility through all top-level headings, all headings, and everything. | org-shifttab                            |
| C-c C-n       | Go to next heading                                                             | org-next-visible-heading                |
| C-c C-p       | Go to previous heading                                                         | org-previous-visible-heading            |
| C-c C-f       | Go to next heading of same level                                               | org-forward-heading-same-level          |
| C-c C-b       | Go to previous heading of same level                                           | org-backward-heading-same-level         |
| C-c C-u       | Go to parent heading                                                           | outline-up-heading                      |
| C-c C-j       | Go to …                                                                        | org-goto                                |
| M-RET         | Add a heading below or before current heading                                  | org-meta-return                         |
| C-u M-RET     | Add a heading after current subtree                                            | org-meta-return                         |
| C-u C-u M-RET | Add a heading at the end of the parent subtree                                 | org-meta-return                         |
| C-RET         | Add a heading after the current subtree                                        | org-insert-heading-respect-content      |
| M-S-RET       | Add a TODO heading below or before current heading                             | org-insert-todo-heading                 |
| C-S-RET       | Add a TODO heading after current subtree                                       | org-insert-todo-heading-respect-content |
| C-c \*        | Toggle heading for current line or region                                      | org-ctrl-c-star                         |
| C-c C-t       | Toggle TODO on current heading                                                 | org-todo                                |
| M–            | Cycle the thing at point                                                       | org-shiftleft                           |
| M-+           | Cycle the thing at point                                                       | org-shiftright                          |
| M-n           | Cycle the thing at point                                                       | org-shiftdown                           |
| M-p           | Cycle the thing at point                                                       | org-shiftup                             |
| C-c C-s       | Add scheduled date                                                             | org-schedule                            |
| C-c C-d       | Add deadline                                                                   | org-deadline                            |
| \<M-up\>      | Move current subtree up                                                        | org-metaup                              |
| \<M-down\>    | Move current subtree down                                                      | org-metadown                            |
| \<M-left\>    | Promote current heading by one level                                           | org-metaleft                            |
| \<M-right\>   | Demote current heading by one level                                            | org-metaright                           |
| \<M-S-left\>  | Promote current subtree by one level                                           | org-shiftmetaleft                       |
| \<M-S-right\> | Demote current subtree by one level                                            | org-shiftmetaright                      |
| M-h           | Select current element (and subsequent elements)                               | org-mark-element                        |
| C-c @         | Select current subtree (and subsequent subtrees)                               | org-mark-subtree                        |
| C-c C-x C-w   | Kill subtree (and the next N subtrees)                                         | org-cut-special                         |
| C-c C-x M-w   | Copy subtree (and the next N subtrees)                                         | org-copy-special                        |
| C-c C-x C-y   | Yank subtree                                                                   | org-paste-special                       |
| C-c C-x c     | Clone subtree                                                                  | org-clone-subtree-with-time-shift       |
| C-c C-x b     | Show the current subtree in an indirect buffer                                 | org-tree-to-indirect-buffer             |
| C-c ^         | Sort same-level entries                                                        | org-sort                                |
| C-c /         | Search and show results in a sparse tree                                       | org-sparse-tree                         |
| M-g n         | Go to next match in sparse tree                                                | next-error                              |
| M-g p         | Go to previous match in sparse tree                                            | previous-error                          |
| C-c C-c       | While in sparse tree view, abort matching hightlights                          | org-ctrl-c-ctrl-c                       |
| C-c C-x d     | Insert a drawer. `C-u ~` to insert a property drawer                           | org-insert-drawer                       |

### Lists

| Keys                | Meaning                                                                   | Command                       |
| ------------------- | ------------------------------------------------------------------------- | ----------------------------- |
| M-RET               | Insert an item of same level on next line.                                | org-meta-return               |
| \<M-up\>            | Move item and its children up to the same level.                          | org-metaup                    |
| \<M-down\>          | Move item and its children down to the same level.                        | org-metadown                  |
| \<M-left\>          | Promote item but not its children.                                        | org-metaleft                  |
| \<M-right\>         | Demote item but not its children.                                         | org-metaright                 |
| \<M-S-left\>        | Promote list item and its children.                                       | org-shiftmetaleft             |
| \<M-S-right\>       | Demote list item and its children.                                        | org-shiftmetaright            |
| C-c -               | Toggle bullet presence at current line or region, or cycle bullet styles. | org-ctrl-c-minus              |
| C-c C-\*            | Convert the whole plain list into a subtree of the heading at point.      | org-list-make-subtree         |
| M-S-RET             | Insert an empty checkbox on next line.                                    | org-insert-todo-heading       |
| C-c C-c             | Toggle checkbox status on current item.                                   | org-ctrl-c-ctrl-c             |
| C-u C-c C-c         | Toggle checkbox presence on current item.                                 | ^                             |
| ???                 | Toggle checkbox status for selected region.                               |                               |
| C-u C-u C-c C-c     | Set checkbox to intermediate state `[-]`.                                 | ^                             |
| C-c C-x C-b         | Toggle checkbox status or presence on current item.                       | org-toggle-checkbox           |
| C-u C-c C-x C-b     | Toggle checkbox presence for selected list or list under a heading.       | ^                             |
| C-u C-u C-c C-x C-b | Same as above but set the checkboxes to `[-]`.                            | ^                             |
| C-c C-x o           | Toggle if the checkboxes must be checked off in sequence.                 | org-toggle-ordered-property   |
| C-c \#              | Update the statistics cookie in current heading.                          | org-update-statistics-cookies |
| C-u C-c \#          | Update all cookies in the buffer.                                         | ^                             |

### Links

| Keys        | Meaning                                          | Command            |
| ----------- | ------------------------------------------------ | ------------------ |
| C-c C-l     | Insert or edit link.                             | org-insert-link    |
| C-c C-o     | Follow link.                                     | org-open-at-point  |
| C-c &       | Return to link after following it.               | org-mark-ring-goto |
| C-c C-x C-n | Go to next link. `C-u ~` to go to previous link. | org-next-link      |
| C-c C-x C-p | Go to previous link                              | org-previous-link  |

### Tables

| Keys          | Meaning                                                                     | Command                                 |
| ------------- | --------------------------------------------------------------------------- | --------------------------------------- |
| TAB           | Re-align the table, move to the next field. Creates a new row if necessary. | org-cycle                               |
| S-TAB         | Re-align, move to previous field.                                           | org-shifttab                            |
| C-c C-c       | Re-align the table and don’t move to another field.                         | org-ctrl-c-ctrl-c                       |
| C-c RET       | Create a table with horizontal line or insert a horizontal line below.      | org-ctrl-c-ret                          |
| C-c ¦         | Create a table or convert an active region into a table.                    | org-table-create-or-convert-from-region |
| M-e           | Move to end of the current table field, or on to the next field.            | org-forward-sentence                    |
| M-a           | Move to beginning of the current table field, or on to the previous field.  | org-backward-sentence                   |
| C-c SPC       | Blank the field at point.                                                   | org-table-blank-field                   |
| C-c \`        | Edit field.                                                                 | org-table-edit-field                    |
| C-c C-c       | Exit editing field.                                                         | org-ctrl-c-ctrl-c                       |
| S-RET         | Copy the field at point to the field below.                                 | org-table-copy-down                     |
| \<M-right\>   | Move the current column right.                                              | org-metaright                           |
| \<M-left\>    | Move the current column left.                                               | org-metaleft                            |
| \<M-up\>      | Move the current row up.                                                    | org-metaup                              |
| \<M-down\>    | Move the current row down.                                                  | org-metadown                            |
| \<M-S-left\>  | Delete current column.                                                      | org-shiftmetaleft                       |
| \<M-S-right\> | Insert a new column to the left.                                            | org-shiftmetaright                      |
| C-o           | Insert a new row above.                                                     | org-open-line                           |
| C-c -         | Insert a horizontal line below current row.                                 | org-ctrl-c-minus                        |
| C-u C-c -     | Insert a horizontal line above current row.                                 | ^                                       |
| C-c ^         | Sort the table.                                                             | org-sort                                |
| C-j           | Goto next table row or insert a newline and indent.                         | org-return-indent                       |

### Navigation

| Keys  | Meaning                                                     | Command            |
| ----- | ----------------------------------------------------------- | ------------------ |
| C-c & | Go back to previous position (after following a link etc.). | org-mark-ring-goto |
| C-c % | Put the current position into the mark ring and rotate it.  | org-mark-ring-push |

### Agenda views

| Keys  | Meaning           | Command    |
| ----- | ----------------- | ---------- |
| C-c a | Open agenda views | org-agenda |

In agenda
views:

| Keys | Meaning                                                             | Command         |
| ---- | ------------------------------------------------------------------- | --------------- |
| a    | Open week view. Use prefix arg `C-u <n>` to specify days to display | org-agenda-list |
|      |                                                                     |                 |

In week view:
[ref](info:org#Agenda%20commands)

| Keys      | Meaning                                                           | Command                            |
| --------- | ----------------------------------------------------------------- | ---------------------------------- |
| SPC       | Show original location in another window                          | org-agenda-show-and-scroll-up      |
| TAB       | Go to original location in another window                         | org-agenda-goto                    |
| RET       | Go to the original location of the item and delete other windows. | org-agenda-switch-to               |
| F         | Toggle follow mode                                                | org-agenda-follow-mode             |
| C-c C-x b | Display subtree                                                   | org-agenda-tree-to-indirect-buffer |
| C-c C-o   | Follow a link in the entry                                        | org-agenda-open-link               |
|           |                                                                   |                                    |

## Info mode

| Keys | Meaning      | Command      |
| ---- | ------------ | ------------ |
|      | Clone buffer | clone-buffer |

## Programming

### Project awareness

1.  Projectile
    
    | Keys      | Meaning                                                          | Command              |
    | --------- | ---------------------------------------------------------------- | -------------------- |
    | M-p f     | Find file in current project. `C-u M-p f` to clear cache first.  | projectile-find-file |
    | M-p F     | Find file in all projects                                        |                      |
    | M-p g     | Find file in current project based on context                    |                      |
    | M-p e     | Find recently visited file in project                            |                      |
    | M-p T     | Find test file in current project                                |                      |
    | M-p o     | Find keywords in current project buffers                         |                      |
    | M-p s g   | Find keywords in current project files with `grep`               |                      |
    | M-p s s   | Find keywords in current project files with `ag.el`              |                      |
    | M-p d     | Find directory in current project                                |                      |
    | M-p 4 C-o | Display a project buffer in another window without selecting it  |                      |
    | M-p b     | Switch to project buffer                                         |                      |
    | M-p LEFT  | Switch to previous project buffer                                |                      |
    | M-p RIGHT | Switch to next project buffer                                    |                      |
    | M-p a     | Switch between files with the same name but different extensions |                      |
    | M-p t     | Toggle between an implementation file and its test file          |                      |
    | M-p p     | Open or switch project                                           |                      |
    | M-p D     | Browse project root in dired                                     |                      |
    | M-p v     | Browse project root in vc-dir or magit                           |                      |
    | M-p V     | Browse dirty version controlled projects                         |                      |
    | M-p r     | Replace in current project                                       |                      |
    | M-p S     | Save all project buffers                                         |                      |
    | M-p k     | Kill all project buffers                                         |                      |
    | M-p m     | Invoke a command                                                 |                      |
    | M-p i     | Invalidates the project cache (if existing)                      |                      |
    | M-p R     | Regenerates the projects TAGS file                               |                      |
    | M-p j     | Find tag in project's TAGS file                                  |                      |
    | M-p E     | Open the root dir-locals-file of the project                     |                      |
    | M-p \!    | Run shell-command in the root directory of the project           |                      |
    | M-p &     | Run async-shell-command in the root directory of the project     |                      |
    | M-p E     | Opens the root dir-locals-file of the project                    |                      |
    | M-p z     | Add the currently visited file to the cached                     |                      |
    | M-p C-h   | View all projectile key-bindings                                 |                      |
    

2.  Treemacs
    
    | Keys      | Meaning                                      | Command                |
    | --------- | -------------------------------------------- | ---------------------- |
    | C-x t     | Initialize or toggle treemacs                | treemacs               |
    | C-c t     | Select treemacs window                       | treemacs-select-window |
    | C-c C-p ? | Show keys relating to project administration |                        |
    |           |                                              |                        |
    

### Navigation

| Keys    | Meaning                                    | Command                            |
| ------- | ------------------------------------------ | ---------------------------------- |
| M-.     | Find or go to definition                   | xref-find-definitions              |
| C-x 4 . | Find or go to definition in another window | xref-find-definitions-other-window |
| M-?     | Find references to the identifier at point | xref-find-references               |
| M-S-s   | Find references to the identifier at point | lsp-find-references                |
| M-h     | Go to next reference                       | lsp-ui-find-next-reference         |
| M-S-h   | Go to previous reference                   | lsp-ui-find-prev-reference         |
| M-.     | Go to implementation                       | lsp-goto-implementation            |
| C-\<    | Go to super                                | lsp-java-open-super-implementation |
| M-n     | Go to next error                           | flymake-goto-next-error            |
| M-p     | Go to previous error                       | flymake-goto-prev-error            |

### Documentation

| Keys    | Meaning                                                               | Command                 |
| ------- | --------------------------------------------------------------------- | ----------------------- |
| M-;     | Insert or indent comment on current line `C-u ~` to kill the comment. | comment-dwim            |
| M-j     | Continue comment on another line                                      | indent-new-comment-line |
| C-x C-; | Comment or uncomment current line                                     | comment-line            |

### Magit

| Keys         | Meaning                                               | Command                          |
| ------------ | ----------------------------------------------------- | -------------------------------- |
| C-x g        | Open magit buffer ([Def](emacs.org::*Installation))   | magit-status                     |
| C-c g        | Show transient command list buffer from any buffer.   | magit-file-dispatch              |
| h,?          | Show command list in a transient buffer.              | magit-dispatch                   |
| TAB          | Expand or collapse section at point.                  | magit-section-toggle             |
| C-TAB        | Cycle visibility of current section and its children. | magit-section-cycle              |
| s            | Stage changes.                                        | magit-stage-file                 |
| u            | Unstage changes.                                      | magit-unstage-file               |
| c            | Show commit buffer.                                   | magit-commit                     |
| \- c         | Commit changes and show commit message buffer.        | magit-commit-create              |
| \- - C-c C-c | Submit commit message.                                |                                  |
| P            | Show push commands transient buffer.                  | magit-push                       |
| \- p         | Push commits.                                         | magit-push-current-to-pushremote |
| F            | Show pull commands transient buffer.                  | magit-pull                       |
| \- p         | Pull commits.                                         | magit-pull-from-pushremote       |
| q            | Quit status buffer.                                   | magit-mode-bury-buffer           |

### Automation

| Keys   | Meaning                 | Command           |
| ------ | ----------------------- | ----------------- |
| M-/    | Auto-completing         | dabbrev-expand    |
| C-f5   | Format buffer           | lsp-format-buffer |
| C-S-f5 | Format region           | lsp-format-region |
| C-f2   | Rename                  | lsp-rename        |
| C-c c  | Show company candidates | company-complete  |

1.  Company mode
    
    After the suggestion window is started, run the following commands
    to select or navigate through the
    candidates.
    
    | Keys     | Meaning                                        | Command |
    | -------- | ---------------------------------------------- | ------- |
    | M-n      | Move highlighting down                         |         |
    | M-p      | Move highlighting up                           |         |
    | C-v      | Next page                                      |         |
    | M-v      | Previous page                                  |         |
    | C-s      | Search for candidates                          |         |
    | C-M-s    | Filter candidates                              |         |
    | M-0 .. 9 | Select the N-th candidates (1)                 |         |
    | C-h/F1   | Show doc of highlighted item in another buffer |         |
    | C-g      | Abort                                          |         |
    

### Run/Debug

| Keys   | Meaning | Command           |
| ------ | ------- | ----------------- |
| C-f9   | Debug   | dap-debug         |
| C-S-f9 | Restart | dap-debug-restart |

### Verb

Keys below are used after prefix keys `C-c
C-r`.

| Keys | Meaning                                                                | Command                                      |
| ---- | ---------------------------------------------------------------------- | -------------------------------------------- |
| C-r  | Send request. `C-u C-c C-r C-r` to see complete request before sending | verb-send-request-on-point-other-window-stay |
| C-f  | Resend request.                                                        | verb-send-request-on-point                   |

# Custom key-bindings

  - <span id="newline-below-without-break">newline-below-without-break</span> and <span id="newline-above-without-break">newline-above-without-break</span>
    
    ``` elisp
    ;; Open new line below current line without breaking current line
    (defun newline-below-without-break ()
    "1.Move to end of line; 2. Insert newline with index"
    (interactive)
    (let ((oldpos (point))) (end-of-line) (newline-and-indent)))
    (global-set-key (kbd "<S-return>") 'newline-below-without-break)
    
    ;; Open new line above current line without breaking current line
    (defun newline-above-without-break ()
    "Insert an empty line above the currentline. Position the cursor at its beginning, according the current mode"
    (interactive)
    (move-beginning-of-line nil)
    (newline-and-indent)
    (forward-line -1)
    (indent-according-to-mode))
    (global-set-key (kbd "<C-S-return>") 'newline-above-without-break)
    ```

  - <span id="xah-forward-block">xah-forward-block</span> and <span id="xah-backward-block">xah-backward-block</span>
    
    ``` elisp
    ;; Move to next blank line separated block
    (defun xah-forward-block (&optional n)
    "Move cursor beginning of next text block.
    A text block is separated by blank lines.
    This command similar to `forward-paragraph', but this command's behavior is the same regardless of syntax table.
    URL `http://ergoemacs.org/emacs/emacs_move_by_paragraph.html'
    Version 2016-06-15"
    (interactive "p")
    (let ((n (if (null n) 1 n)))
    (re-search-forward "\n[\t\n ]*\n+" nil "NOERROR" n)))
    (global-set-key (kbd "M-]") 'xah-forward-block)
    
    ;; Move to previous blank line separated block
    (defun xah-backward-block (&optional n)
    "Move cursor to previous text block.
    See: `xah-forward-block'
    URL `http://ergoemacs.org/emacs/emacs_move_by_paragraph.html'
    Version 2016-06-15"
    (interactive "p")
    (let ((n (if (null n) 1 n))
          ($i 1))
          (while (<= $i n)
          (if (re-search-backward "\n[\t\n ]*\n+" nil "NOERROR")
          (progn (skip-chars-backward "\n\t "))
          (progn (goto-char (point-min))
          (setq $i n)))
          (setq $i (1+ $i)))))
    (global-set-key (kbd "M-[") 'xah-backward-block)
    ```

# Functions

format, user-full-name, read-string
