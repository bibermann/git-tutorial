# [Git Tutorial](../README.md)

## [<small>1</small> Learning](README.md)

### <small>1.2</small> Tasks to know

You should know the following tasks.
For each task, try to think about how to achive it and then open the solution to check yourself.

<details><summary>How to reset your local branch to the (rebased) remote branch</summary><p>

- Have a clean working directory.
- Use `git reset --hard origin/BRANCH`

</p></details>

<details><summary>How to re-use the commit message after resetting to a previous commit</summary><p>

- Reset to previous commit: `git reset [--hard] HEAD~`
- Work with non-dangerous commands in Git, including commits.
- Re-use the message with: `git commit -c ORIG_HEAD`

</p></details>

---
[« <small>1.1</small> Commands to know](1-commands.md) | <small>1.2</small> Tasks to know
