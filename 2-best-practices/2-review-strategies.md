# [Git Tutorial](../README.md)

## [<small>2</small> Best practices](README.md)

### <small>2.2</small> Review strategies

#### Preparing a PR/MR

Even if you know the person who will review your request, try to think about a **new** developer in your team
trying to understand what you have done and why.
They will go through your changes commit by commit
so provide them a concise but comprehensible journey through your work.

Before sending a pull/merge request, please make sure
that your commit messages are well-formed and adjust them if necessary
(see also [<small>2.1.1</small> Writing good commit messages](1.1-commit-message.md)).
You may also need to squash some of your commits into single ones.

##### Squashing commits

While working, it may be convenient to commit more frequently with work-in-progress commits.
There are plenty of valid reasons why you would do that: Commits you may eventually want to undo in future,
experimenting with changes, adding fixups you want to rebase later etc.

Other team members may also commit to the work-in-progress branch.

You do not want this granularity in the final branch.
The easiest method for cleaning up the commits is *interactive rebasing*.
Git provides `git rebase -i LAST_GOOD_COMMIT` or `git rebase -i --root` for this.

When doing a fixup or a squash, please make sure that you do **not** join commits from different authors.
You could add a `Co-Authored-By` trailer for giving contribution to another person,
but this is less granular and not part of git metadata (author and committer are).
It sometimes helps when you know exactly which person has made which change,
f.ex. when you have questions to a specific change or to be able to evaluate the code
in using the known knowledge/background of the person who made the change.

#### Merging

Merge commits are holding commits together which are, as part of a more general task, somehow connected.
This information may be imporant to understand the context of a commit.

That's why, in general, you should have a good reason before doing a fast-forward merge.
Normally you should  avoid this and give `--no-ff` to the `merge` command to create a merge commit
even if fast-forward would be possible (which always is when you have rebased).

##### Merging complex branches

In the [previous chapter](1-general.md) we learned, that we should always rebase before doing a merge.
If the history beeing rebased contains merge commits, make sure to give `-p` or `--preserve-merges`
when issuing the `rebase` command. Else merge commits would not get replayed.

---
[« <small>2.1</small> General](1-general.md) | <small>2.2</small> Review strategies | [<small>2.3</small> Working with GitLab »](3-gitlab.md)
