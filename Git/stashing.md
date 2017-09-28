# Stashing Changes

`git stash` is useful for pausing in-progress work that isn't ready to be
commited yet.


## Snapshotting and Stashing Changes

`git stash`
Without any arguments, this command will record a snapshot of the staged and 
unstaged changes and then clear the working directory.

`git stash -p`
Passing the `--patch` flag to the command will iterate through each changed hunk
in the working dir and ask if it should be stashed.

### Hunk Commands

`?` 
Help, used to view full list of hunk commands.

`/` 
Search for a hunk with regex

`n`
Don't stash current hunk

`q`
Quit iterating through hunks and stash all selected hunks

`s` 
Split hunk into smaller hunks

`y`
Stash this hunk

## View Stashed Snapshots 

`git stash list`
This command lists all saved snapshots in the stash stack.

`git stash show`
This command will show diffs for the stash and the current working dir.
Use the patch `-p` flag to view the full diff of a stash. 

## Applying Stashed Changes

`git stash pop` 
This command will applies the most recently stashed changes to the working 
directory and remove it from the stash stack.

`git stash apply <stash name>`
This command applies the named stash to the working dir, but does not remove the 
snapshot from the stash stack. If no name is given, then the most recent
snapshot is appiled.

### Creating a New Branch from a Stashed Snapshot

`git stash branch <branch-name> <stash-name>`
This command checks out a new branch based on the commit the stash was created 
on top of, then pops the specified stash changes on top.


## Removing a Snapshot from the Stack

`git stash drop <stash name>`
This command will remove the <named> snapshot from the stash stack.

`git stash clear`
This command removes all snapshots from the stash stack.


