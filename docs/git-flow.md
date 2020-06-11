## Git Workflow
The Git workflow that we used is almost identical to the Gitflow Workflow popularized by Vincent Driessen

See: https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow

In Ralali, the flow is slightly modified. The main points are:
1. There are mainly 3 branches:
    - master
    - staging
    - development

## Table of contents
  - [Creating Feature Branch](#creating-feature-branch)
  - [Pull Request](#pull-request)
    - [Development](#development)
    - [Staging](#staging)
  - [Releasing](#releasing)
    - [Staging](#staging)
  - [Takedown Feature Branch](#takedown-feature-branch)
  - [Undo Feature Branch](#undo-feature-branch)
  
## Creating Feature Branch
Create branch based on `master` branch
   
``` bash
$ git fetch --prune
$ git checkout master (if your location not at master)
$ git checkout -b feature-a
$ git checkout -b feature-a origin/master (if your location not at master)
```

Make some changes

Push to your repository
   
``` bash
$ git push origin feature-a
```

## Pull Request
Before you PR, make sure your code is already okay.

### Development
Before you PR to branch `development`. Freeze your branch by creating a new branch based on your branch you have been created.

``` bash
$ git fetch --prune
$ git checkout development
$ git pull origin development
$ git checkout feature-a
$ git checkout feature-a-dev
$ git merge development
$ git push origin feature-a-dev
```

Then you created PR from `feature-a-dev` to `development`

### Staging
Before you PR to branch `staging`. Freeze your branch by creating a new branch based on your branch you have been created.

``` bash
$ git fetch --prune
$ git checkout staging
$ git pull origin staging
$ git checkout feature-a
$ git checkout feature-a-stg
$ git merge staging
$ git push origin feature-a-stg
```

Then you created PR from `feature-a-stg` to `staging`

> In your pull request, don't forget to add 
``` md
- Title [this can be your ticket title]
- Description
  - What's your changes
  - Link Figma (Optional)
  - Link Ticket on trello
  - Screenshot Before and After
- Reviewer
- Label
- Release version milestone
```

## Releasing
For release, you can release from `staging` branch or you can freeze branch `staging` to a new branch depend on features that you want to release

### Staging
Before creating a release, make sure your code is already okay in `staging`

Freeze your codes first before PR by creating `release/*` branch (e.g. `release/1.0.0`) based on `staging` branch
  
``` bash
$ git fetch --prune
$ git checkout staging
$ git pull origin staging
$ git checkout -b release/1.0.0
$ git push origin release/1.0.0
```

Pull request the `release/*` branch to `master` branch

Tag the `master` branch
   
``` bash
$ git tag -a v1.0.0 -m "v1.0.0"
$ git push origin v1.0.0
```

Release the app from the `master` branch

## Takedown Feature Branch
Takedown your feature branch that is't used in release version

Open your pull request page

Click `Revert` and github will automatically create a revert branch

Pull request the `revert-feature` branch to `staging` branch

## Undo Feature Branch
Undo your feature branch that will used in release version

Switch to your feature branch

``` bash
$ git checkout feature-a
```

Find commit id

``` bash
$ git log
```

Undo your feature branch

``` bash
$ git revert COMMIT-ID
```

Push to your repository
   
  ``` bash
  $ git push origin feature-a
  ```

From your repository, pull request to `staging` branch
