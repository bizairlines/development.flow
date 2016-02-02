# Development Flow

## Version
0.1.0

## Project Versioning
When versioning projects you should consider the following practice:
http://semver.org/

## Git Flow
Originally based on [Atlassian GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow).

The following branches must be created for every projects available:
* master
* hotfix
* develop
* feature/*
* release

### Master
This branch is **BLOCKED** and only users with *admin* permission are allowed to commit and push to it. 

After QA'ing thouroughly the branches/features mush be merged with it.

*Note*: The deployement to production must be done from this branch.

### Hotfix
This branch should be used in cases to fix critical bugs. `hotfix` branches are created from the `master` branch. 

Let's say, for example, that version 1.2.0 is the current version of the application running live and it's causing troubles due to a severe bug, but you're working on a branch and it's not stable. 

We must checkout to `hotfix` branch, pull the latest modifications from `master` and start fixing the problem:
```
$ git checkout -b hotfix
Switched to a new branch "hotfix"
$ git pull origin master
```
After done the fixes, commit to `hotfix` branch:
```
$ git commit -a -m "Bumped version number to 1.2.1"
[hotfix 41e61bb] Bumped version number to 1.2.1
1 files changed, 1 insertions(+), 1 deletions(-)
```
After the commit it's time to push the work to the remote server:
```
$ git push origin hotfix
```

**DO NOT** checkout to this branch from different branch then `master`.

### Develop
At the mostly cases this would be the most recent branch. This branch can be used for fast developments and codes and with low impact in the project.

For example, if you're changing messages in a `i18n` file, it's not necessary to create a `feature/*` branch for it.

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
