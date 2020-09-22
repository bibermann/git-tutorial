# [Git Tutorial](../README.md)

## [Best practices](README.md)

### General

- Configure your terminal/prompt so that you always see:
    - Current local branch name.
    - Git status (how local and remote branches have diverged, working tree status etc.).
- Do ***not*** use `git pull` (*1). Use `git fetch; git merge --ff-only origin/BRANCH` instead. That way you get an error if the remote branch was rebased. Else an unwanted merge-commit gets created, which, in case the remote branch was rebased, could re-introduce unwanted changes.
- Pay attention when force-pushing:
    - Do ***not*** use `git push -f` or `git push --force` on branches where others may also push to.
    - Alternatively you may use `git push --force-with-lease`, which refuses to push if the remote branch has been updated from the current point of view of your repository, i.e. if the upstream remote branch is no longer in sync with your local copy of the remote branch. ***Be aware*** that `git fetch` will sync this, so a `git fetch` followed by a `git push --force-with-lease` will ***not*** protect you overriding changes from other committers. If you have rebased a remote branch and really need to `git fetch` before `git push --force-with-lease`, make sure to read the output of `git fetch` to see whether the remote branch has changed in the meantime.
- Checkout new remote branches with `-t` or `--track` to correctly configure pull/push commands and seeing the Git status in your terminal/prompt.
- To reset your local branch to the (rebased) remote branch:
    - Have a clean working directory.
    - Use `git reset --hard origin/BRANCH`
- Make yourself familiar with interactive rebasing.
- Never use Git features of your IDE or another tool, if you do not exactly know to wich Git commands the tool action would map. Otherwise it is difficult to de-mystify and learn understanding Git, which is necessary for more complex problems or situations that may arise.

Remarks:
- *1) You may use `git pull` if local branch and upstream remote branch have not diverged, i.e. you have no unpushed commits and the remote branch was not rebased (if unsure, call `git fetch` and see Git status).
