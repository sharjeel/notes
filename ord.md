# org-mode

## Basics

Quick Ref: http://orgmode.org/orgcard.pdf

`TAB` Cycle Subtree

`M-<up>` Move up

`M-<down>` Move down

`M-<left>` Promote

`M-<right>` Demote

`M-RET` Insert new heading/item at current level

`C-RET` Insert new heading/item after subtree

`C-c -` Change Item bullet types

Record position: `C-%`

Move to recorded position: `C-&`


## Sparse Trees

`C-c /` Prompt

`C-c / r` Regex base sparse tree

## Links

Footnote:

```
The org notes [fn:1]
...blablabla
...blablabla
[fn:1] The link is http://github.com/sharjeel/notes
```

Editing: `C-c C-1`
Following: `C-c C-o`

Internal Links:

```
[[target][target description]]
Or [[target]]
..    
<<target>>
```

External Links:

```
http://linkwillfollow/
[[http://explicitlink]]
[[http://explicitlink][Explicit LinkDescription]]
[[file:~/workspace/tmp/code.c::225]]
[[file:~/Desktop/todo.org::stale-bugs][Long overdue TODO]]
[[file:~/workspace/project/Tests.java::/void.*setup\(\)/]Tests]]
```

## TODO

```
TODO

* TODO Organize Birthday [50%]                  :home:
  - [-] Get Balloons 
  - [ ] Get Cake
* TODO Another Todo [1/3]
   - [ ] Pending 1
   - [-] Done 1
   - [ ] Pending 2
* DONE Fix door :home:
```

## Tables

Any line with starting with `|` as first non-whitespace character is considered part of a table.

e.g. 

 *  ```
    |Name|Age|Location|
    |-
    ```

	and pressing tab,
    or simply

    ```|Name|Age|Location``` and `C-c RET`
    
    would expand it in a table
    
* `Tab` Move to next field
* `S-Tab` Move to previous field
* `C-c |` Converts region into table. Could be CSV or tab separated
* `C-c C-c` Re-align the table.
* `RET` Re-align the table and move down to next row. Creates a new row if necessary.

### Column and row editing

`M-left`

`M-right`   Move column left/right

`M-S-left`    Kill the current column

`M-S-right`    Insert a new column to the left

`M-up/down`    Move row up or down

`M-S-up`    Kill the current row

`M-S-down`    Insert a new row above.

`C-c -`    Insert a horizontal line

`C-c RET`    Insert horizontal line and move below.

`C-c ^`    Sort the table lines in the region. Current position indicates the column.

