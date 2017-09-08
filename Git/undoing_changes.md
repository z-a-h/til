# Undoing Changes

## Checkout 

`git checkout`
Change the working dir to match the specified commit

`git checkout HEAD`
Go back to the most recent commit 


## Revert 

A safe way to undo changes, but appending a commit undoing the current state.

`git revert` 
Undoes a commited snapshop and appends a new commit with the
resulting content, to prevent Git from losing history


## Reset 

A command for undoing changes permenantly. 

### BE VERY CAREFUL WHEN USING `--hard`!!! ONLY USE WHEN SOBER AND SOMETHING HAS
GONE HORRIBLY WRONG

### DON'T RESET PUBLIC HISTORY

`git reset <file>` 
Removes a file from the staging area, unstaging a file
without changing the working dir

`git reset`  
Reset the staging area to the most recent commit. Unstages all
files without overwriting any changes

### BE CAREFUL: YOU CAN'T UNDELETE
`git reset --hard`
OBLITERATES ALL UNCOMMITTED CHANGES
Reset the staging area AND working dir to match most recent
commit.

`git reset <commit>`
Moves current branch backward to commit and resets staging
area.  Working dir is not changed. Lets you re-commit history using cleaner,
more atomic snapshots.

### BE CAREFUL: YOU CAN'T UNDELETE
`git reset --hard <commit>`
OBLITERATES ALL UNCOMMITED CHANGES AND COMMITS AFTER <COMMIT>
Moves branch tip backward to commit AND resets BOTH
staging AND working dir.  


## Clean Up
 
### NOT UNDOABLE 
Remove untracked files from the working directory. 

`git clean -n` 
Show all files that would be removed by using `git clean`

`git clean -f` 
Remove all untracked files from current dir. Does not remove untracked folders
or ignored files

`git clean -f <path>` 
Remove all untracked files from path

`git clean -df`
Remove untracked files AND untracked dirs

`git clean -xf`
Remove all untracked files AND ignored files
