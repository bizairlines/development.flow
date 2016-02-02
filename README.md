# Development Flow

## Version
0.1.0

## Project Versioning
When versioning projects you should consider the following practice:
http://semver.org/

## Git Flow
Originally based on [Atlassian GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) and [Vicent Driessen](https://github.com/nvie).

The following branches must be created for every available projects and also for new projects:
* master
* hotfix
* develop
* feature/*
* release

### Master
This branch is **BLOCKED** and only users with *admin* permission are allowed to commit and push to it. 

*Note 1*: There're only 2 branches that are allowed to merge to `master`: `develop` and `hotfix`. All of the others **MUST** merge to `develop`, QA it thorougly and then merge `develop` to `master`.

*Note 2*: The deployement to production must be done from this branch.

### Develop
At the mostly cases it'll be the most recent branch. It can be used for:

1. Fast developments and codes with low impact to the project, and;
2. To QA a sprint before it's launch.

For example, if you're changing messages in a `i18n` file then it's not necessary to create a `feature/*` branch for it.

*Note*: The merge to `develop` are allowed only after a thouroughly QA.

### Hotfix
This branch should be used in situations of critical bugs.

Let's say, for example, that version 1.2.0 of an application has a severe bug, but you're working on a different branch and it's not stable yet, so you **MUST** do the fix in `hotfix` and then merge back to `master`. 

To do this, you must checkout to `hotfix` branch, pull the latest updates from `master` and start fixing the problem:
```
$ git checkout -b hotfix
Switched to a new branch "hotfix"
$ git pull origin master
```
When the fixes are done, commit to `hotfix` branch:
```
$ git commit -a -m "Bumped version number to 1.2.1"
[hotfix 41e61bb] Bumped version number to 1.2.1
1 files changed, 1 insertions(+), 1 deletions(-)
```
Now it's time to push the work to the remote server:
```
$ git push origin hotfix
```

### Feature
New features must be done in this branch.

For example, if you're creating a new code to handle user's sessions, you should do this here.

This branch **MUST** use the following pattern: `feature/{id}-name-of-the-feature`, where `id` is the number of the card at [Jira](https://bizairlines.atlassian.net/) or an another project/issue tracker.

```
$ git checkout -b feature/5532-redis-integration develop
Switched to a new branch "feature/5532-redis-integration"
```
After done the improvements, commit to the branch you're working on:
```
$ git commit -a -m "New feature"
[feature/5532-redis-integration 42ka1bb] New feature
1 files changed, 1 insertions(+), 1 deletions(-)
```
After the commit it's time to push it to remote server:
```
$ git push origin feature/5532-redis-integration
```

### Release
`@todo`

### Tags
After every successfull deploy the project **MUST** be tagged.

```sh
$ git checkout master
$ git tag -a v1.2.1 -m 'Some comment is necessary'
$ git push origin v1.2.1
```

## Author
[Hudson Dunice](https://github.com/dunice)
