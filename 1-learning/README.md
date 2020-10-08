# [Git Tutorial](README.md)

## <small>1</small> Learning

### Dive into Git

Go to https://try.github.io/ and look for the "Learn by reading" and "Learn by doing" sections.

Browse the "Pro Git book" at https://git-scm.com/book.

### Strengthen your knowledge

Make sure you are familiar with the following terms:
- working tree = workspace known to git
- staging area = stage = index
- local vs. remote (upstream) repository
- [tracked/untracked file](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)
- [commit vs. revision](https://stackoverflow.com/a/11792712/704821)

Make yourself familiar with `git reflog`,
[see here](https://stackoverflow.com/a/17860179/704821) for a short introduction.

Make yourself familiar with [interactive rebasing](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History).

Some useful revisions to know:
- `HEAD`: references the current commit
- `ORIG_HEAD` vs. `HEAD@{1}`: See https://stackoverflow.com/a/967611/704821
- [naked `@`](https://stackoverflow.com/a/17910097/704821): same as `HEAD`
- `@^` and `@~`: references the parent of the current commit
- `@^2`: references the second parent of the current commit (for merge commits)
- `@~2`: references the 2nd generation parent of the current commit, i.e. the parent of the parent
- `@^^^` and `@~~~` and `@~3` are equivalent
- `@{FOO}` when `FOO` is not a number: same as `HEAD@{foo}`
- `@{u}`: the current upstream, e.g. `origin/main`

Hint: You can *de-reference* a revision with `git rev-parse REVISION`.

### Cheat sheets

Some useful cheat sheets:
- [github.com » Git Cheat Sheets](https://training.github.com/)
- devhints.io »
    - [Git branches](https://devhints.io/git-branch)
    - [Git revisions](https://devhints.io/git-revisions)
    - [git log](https://devhints.io/git-log)
    - [Git log format string](https://devhints.io/git-log-format)
    - [Git extras](https://devhints.io/git-extras)
    - [Git tricks](https://devhints.io/git-tricks)

### More

* [<small>1.1</small> Commands to know](1-commands.md)
* [<small>1.2</small> Tasks to know](2-tasks.md)

---
<small>1</small> Learning | [<small>2</small> Best practices »](../2-best-practices/README.md)
