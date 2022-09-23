# Git Rebase Watch

If you're working in a popular repository, you'll know too well the problem where your pull request has gone out of sync with `main`/`master` branch.  
You may now want to rebase your branch to keep it up to date, but doing this every 10 minutes can be a little frustrating.

This helper script does that for you!

It will periodically check the upstream merge root (`master` by default) for changes.

If any are found it will:

- Pull the changes to local branch
- Rebase the current (feature) branch over the changes
- Push the current branch to update the PR - keeping it in sync with the merge root

It is designed to be failsafe and will not push if:

- The current git HEAD has changed since it started watching. E.g. new commits
- The name of the current branch has changed since it started watching
- There are any merge conflicts from rebasing with master
- Any commits have been added to your upstream (PR) branch

## Usage

From your git repsitory directory:

```shell
/path/to/my-git-project$ git-rebase-watch [upstream branch [period]]
```
