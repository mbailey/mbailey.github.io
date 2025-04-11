# Git branches


## Local Branches

- [Rebase a local branch on upstream master](branches/Rebase%20a%20local%20branch%20on%20upstream%20master.md)


## List

**Branches with unmerged changes:**

```shell
git branch --no-merged master
```

**Branches merged into main:**

```shell
git branch --merged master
```

**List branches in order of most recent commit:**

```shell
$ git for-each-ref --sort=-committerdate refs/remotes/ --format="%(refname:short)%09%(committerdate:iso8601)%09%(committername)%09%(subject)" | columnise 
origin/feat-fix                            2023-02-08 17:46:47 +1100  Some Person     Fixing the stack name to make it unique
origin/r53-feat                            2023-02-08 17:15:10 +1100  Another Person  Renaming the file
```

### Maintain standard initial branch

```shell
git config --global init.defaultBranch master
```

## Remote Branches

**Checkout a remote branch:**

```shell
git fetch origin
git checkout BRANCH_NAME 
```

**Delete remote branch**:

```shell
git push --delete <remote_name> <branch_name>
```

**Rename default branch**: 

I don't want to have to remember what the default branch is named.

    git branch -m main master
    git push -u origin master

- [stackoverflow](https://stackoverflow.com/a/69344918/660017)



### Fix a branch where I rebased from upstream and it rewrote the commits

ask> maybe I should create a new branch and cherry pick my four commits into it? Or git reset --hard upstream/main on my branch and then cherry pick my new commits?                          

Yes, that's a cleaner approach! Since you have exactly 4 commits that represent your actual changes, creating a fresh branch would be simpler. Here's how:

```bash
# First make sure you're up-to-date with upstream
git fetch upstream

# Create a new branch from upstream/main
git checkout -b feat/allow-use-of-other-whisper-api-endpoints-take-3 upstream/main

# Cherry pick your 4 commits (in chronological order)
git cherry-pick 9e23254a  # feat: Support custom Whisper API endpoints for voice transcription
git cherry-pick 7891e92a  # feat: Add support for custom Whisper API endpoints with robust key handling
git cherry-pick d448bd8c  # fix: Update test to properly simulate custom API base validation
git cherry-pick b9ad3eba  # refactor: Remove redundant test for custom Whisper API configuration

# Push the new branch to your fork
git push origin feat/allow-use-of-other-whisper-api-endpoints-take-3
```
