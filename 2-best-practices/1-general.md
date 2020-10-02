# [Git Tutorial](../README.md)

## [Best practices](README.md)

### General

<details><summary>Configure your terminal/prompt</summary><p>

So that you always see:
- Current local branch name.
- Git status (how local and remote branches have diverged, working tree status etc.).

If you not already have a heavily configured terminal environment,
you may try out [github.com » biberconf](https://github.com/bibermann/biberconf).


</p></details>

<details><summary>Commit often and write commit messages carefully</summary><p>

To really take advantage of the benefits of a version control system,
it is key to carefully describe the pieces of work you have done.
This makes it easier for reviewers or new developers to understand and verify your code
and helps while merging, especially when conflicts arise.

Basically the structure should be like this:
- *Short subject line*
    - Imperative mood
    - Max 50 characters
- Optional: *Body*
    - Optional: *More detailed description*
        - Max 72 characters per line
    - Optional: *Body meta data*
        - Header-like format
        - See [git.wiki.kernel.org » CommitMessageConventions](https://git.wiki.kernel.org/index.php/CommitMessageConventions) for an (incomplete) list

**Important:** The body has to be separated by an empty line.

Example:
```
Fix something serious

The body should describe what was done and why, but not how.
It should not repeat the subject line - omit the description, if there
is nothing more to say.

Closes: #123
Co-Authored-By: Some Author <some-author@company.com>
```

See [git.wiki.kernel.org » CommitMessageConventions](https://git.wiki.kernel.org/index.php/CommitMessageConventions) for an (incomplete) list of possible trailers.

Further reading:
- [theserverside.com » How to write a Git commit message properly with examples](https://www.theserverside.com/video/Follow-these-git-commit-message-guidelines)

</p></details>

<details><summary>Generally, do not use <code>git pull</code></summary><p>

Use `git fetch; git merge --ff-only origin/BRANCH` instead.
That way you get an error if the remote branch was rebased.
Else an unwanted merge-commit gets created, which, in case the remote branch was rebased, could re-introduce unwanted changes.

You are safe to use `git pull` if:
- You have no unpushed commits.
- Local branch and upstream remote branch have not diverged,
  i.e. none of the branches were rebased before its merge-base
  (if unsure, call `git fetch` and see Git status).
- You know that nobody else will force-push something at this moment.

</p></details>

<details><summary>Pay attention when force-pushing</summary><p>

Do ***not*** use `git push -f` or `git push --force` on branches where others may also push to.

Alternatively you may use `git push --force-with-lease`, which refuses to push
if the remote branch has been updated from the current point of view of your repository,
i.e. if the upstream remote branch is no longer in sync with your local copy of the remote branch.
***Be aware*** that `git fetch` will sync this, so a `git fetch` followed by a `git push --force-with-lease`
will ***not*** protect you overriding changes from other committers.
If you have rebased a remote branch and really need to `git fetch` before `git push --force-with-lease`,
make sure to read the output of `git fetch` to see whether the remote branch has changed in the meantime.

</p></details>

<details><summary>Checkout new remote branches with <code>-t</code> or <code>--track</code></summary><p>

Checkout new remote branches (i.e., branches you have not checked out before) with `git checkout -t BRANCH`.

This is to correctly configure pull/push commands and seeing the Git status in your terminal/prompt.

</p></details>

<details><summary>Push new local branches with <code>-u</code> or <code>--set-upstream</code></summary><p>

Push new local branches (i.e. branches you've created and which were not yet pushed before)
with `git push -u origin/BRANCH`

This is to correctly configure pull/push commands and seeing the Git status in your terminal/prompt.

</p></details>

<details><summary>Selectively and careful use Git features via external tools</summary><p>

Never use Git features of your IDE or another tool,
if you do not exactly know to wich Git command(s) the tool action would map.

Otherwise it is difficult to de-mystify and learn or understand Git,
which will be necessary for more complex problems or situations that may arise.

</p></details>

<details><summary>Always rebase before merging</summary><p>

Merge commits must ***not*** contain any changes and should only serve for grouping batches of work.

Each logical piece of change should be represented by a single commit which holds the respective commit meta data
(commit message, author etc.).
If you merge a worker branch into the main branch and conflicts occur,
the conflict resolution would be part of the merge commit.
This work may be extremely difficult and easily results in failures.
But these failures then are somehow hidden in the merge and unrelated to any logical piece of work.
That means you have no commit message describing the change (as part of the merge commit)
which would allow you to validate the work afterwards.

You can avoid all this mess by rebasing the source branch onto the target branch before doing a `git merge --no-ff`.
Then the conflict resolution moves to the respective commit of the source branch and the logical pieces of change
keep self-contained and are not scattered into some merge commit.
That also means that each bug which may be introduced by the conflict resolution is spottable,
it can easily be identified by going through the commits and validated by reading the commit message.

</p></details>

---
General | [Review strategies »](2-review-strategies.md)
