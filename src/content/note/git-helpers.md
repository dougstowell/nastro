---
title: 'Git Helpers'
pubDate: 2021-07-01 15:00:00
description: 'Git Helpers'
author: 'Doug Stowell'
authorAvatar: '/src/assets/dougs.jpg'
image:
    url: '/src/assets/git.png'
    alt: 'Git Helpers'
tags: ["shell", "spine", "git"]
isPinned: true
---

## General

```text
######## Aliases
sudo nano ~/.gitconfig

[alias]
   s = status
   b = branch
   l = log --pretty=format:"%C(yellow)%h\\ %ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate
   co = checkout
   lc = log -1 HEAD --stat
   p = push
   a = add .
   pod = pull origin develop
   pf = pull --ff-only
```

## Spine Specific

```text
######## Aliases
sudo nano ~/.gitconfig

[alias]
   s = status
   b = branch
   l = log --pretty=format:"%C(yellow)%h\\ %ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate
   co = checkout
   lc = log -1 HEAD --stat
   p = push
   a = add .
   pod = pull origin develop
   pf = pull --ff-only

# Create a new branch and Jenkins jobs
git checkout develop
git pull --ff-only
git new-feature dost2-PCRM-3654-remove-pds-edit-orange-buttons

# Commit then fill in the changes.
git commit -a
git push

# Reset all local changes
git checkout .

# Pull latest develop into your branch
git pull origin develop
git push

# Create a UI build example for SRS.
/home/spineii-user/spineii/dev/spinecore/build/createjenkinsjobs.py dost2-PCRM-2763-update-css-cohort --ui spinereportingservice

/home/spineii-user/spineii/dev/spinecore/build/createjenkinsjobs.py dost2-SPII-33030-invalidPatient-intermittent --ui demographicspineapplication


# Finishing up a branch
git push
git checkout develop
git pull
git flow feature finish dost2-PCRM-3089-wds-cohort-informally-dead

####### git flow feature finish dost2-merge-20201202

##### IF CREATING A MERGE BRANCH
git checkout develop
git pull --ff-only

git new-feature dost2-merge-20210219

git pull origin feature/dost2-SPII-33030-invalidPatient-intermittent --ff-only
git pull origin feature/dost2-SPII-32732-intm-sar-patient --ff-only

git push

# Resolve any conflicts.

git push

######## git flow feature finish dost2-merge-20201202-889-3121

##### DELETE BRANCHES
# delete branch locally
git branch -d feature/dost2-merge-20201202-889-3121
# delete branch locally force (even if not been merged yet)
git branch -D feature/dost2-merge-20201202-889-3121

# delete branch remotely
git push origin --delete feature/dost2-merge-20201202-889-3121

=========================================

# SEE IF BRANCHES ARE IN SYNC WHERE HAD HOTFIX AND DEVELOP CHANGES
# Create a local branch and merge the hotfix changes in.
git checkout develop
git pull
git branch feature/dost2-PCRM-3139-cerv-extract-diffs
git checkout feature/dost2-PCRM-3139-cerv-extract-diffs

git merge hotfix/_r21000_blockingFixesBranch008

# Check if any changes are in that hotfix that was not in develop.
git status
# NONE, output is:
# branch feature/dost2-PCRM-3139-cerv-extract-diffs
# nothing to commit, working directory clean

# Tidy Up - delete local and remote branches
git checkout develop
git branch -D feature/dost2-PCRM-3139-cerv-screen-extract
git push origin --delete feature/dost2-PCRM-3139-cerv-screen-extract


# REVERT A FILE BACK TO ITS ORIGINAL - REMOVE ALL CHANGES
git checkout HEAD~ filename

```
