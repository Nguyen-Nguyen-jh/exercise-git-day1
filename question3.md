### If someone accidentally merges a feature (feature/delete-user) onto production and has a list of commitId ended with (0492978, fc9348c, k101100), then another commit (a1fsas8) is added on top of the production branch. How do we remove that merged feature?

1. git revert:

- When you want to create a new commit to undo changes from wrong commits
- git revert will create a new commit that reverses the changes, preserving history without changing the past
