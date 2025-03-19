### If someone accidentally merges a feature (feature/delete-user) onto production and has a list of commitId ended with (0492978, fc9348c, k101100), then another commit (a1fsas8) is added on top of the production branch. How do we remove that merged feature?

1. git revert:

- When you want to create a new commit to undo changes from wrong commits
- git revert will create a new commit that reverses the changes, preserving history without changing the past

2. git reset:

- When you want to completely remove unwanted commits from the history and go back to the state before the commits were merged.
- git reset will change the commit history of the production branch, and you need to make sure that these changes do not affect others.

git reset --soft <commitID_C> (Keep changes in working directory)
git reset --hard <commitID_C> (Discard changes in working directory)

3. git relog

- When you need to retrieve previous states but don't remember the commit ID.
- git reflog records every change in branches and allows you to find previous states to perform reverts or resets.
