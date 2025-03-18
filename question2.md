### If we have a feature branch that hasn't been merged to production and that branch has a bug, what course of action are you going to do with Git before resolving the bug?

1. Create a bugfix branch from the feature branch:

- When you want to continue developing a feature but need to fix a bug during development.
- Creating a new branch from the buggy feature branch will help you keep your evolving changes intact while fixing the bug

2. Create a branch from master or develop to fix the bug:

- If the bug to be fixed is too serious and you don't want to affect the feature development progress
- Create a new branch from master or develop to resolve bugs without affecting the unfinished feature branch.

3. Use the git cherry-pick command to apply some bugfix commits to the feature branch

- When you just want to apply bugfix commits without changing the entire branch
- Save time and focus only on the necessary commits without affecting other parts
