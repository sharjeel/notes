Git 
===


### Browse a file's history

`git log -p file_name`

With file renames:

`git log -p --follow file_name`

### Diffs

Between two branches

`git diff branch1 branch2 -- file_name`

Between current file and another branch

`git diff branch -- filename`

Between current file and a revision

`git diff <revisionid>:file_name file_name`

Diff only filenames

`git diff --name-status`

Diff only filenames between two branches

`git diff --name-status brach1..branch2`

Dif between five revisions back

`git diff HEAD HEAD~n`

Show file from another branch

`git show branch:./path/to/file`

### Undo

Undo last commit with changes staged

`git reset --soft 'HEAD~1'`

Undo last commit with changes discarded

`git reset --hard HEAD~1`

Undo soft reset

`git reset HEAD@{1}`

