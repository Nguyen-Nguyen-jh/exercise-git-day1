### When creating a new feature, what branch should we base it on and why?

1. Create branch from master (for experimental features):

- If the new feature is in the experimental (thử nghiệm) development phase and needs to be tested, test it in a test environment.
- Master is a branch that contains experimental features for the test site, helping you ensure the feature works as expected before pushing to the production environment.

git checkout master
git checkout -b <feature-branch-name>

2. Create a branch from develop:

- If there is a develop branch in the GitFlow workflow, new features will be developed on develop instead of master.
- Develop contains all the features that are being developed and tested in the test environment, ready to be merged into master.

git checkout develop
git checkout -b <feature-branch-name>

3. Create a branch from production (in case you need to test and develop a feature that is ready to deploy):

- If the feature is almost complete and you want to test it in a production test environment.
- Ensure features are tested in close-to-production environments before going live

git checkout production
git checkout -b <feature-branch-name>
