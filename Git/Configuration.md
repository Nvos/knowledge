---
tags:
  - git
  - configuration
---

- `pull.rebase true` is used to avoid accidentally creating merge commit on `git pull`, pretty much it adds `--rebase` to every `git pull`
- `merge.conflictstyle zdiff3` shrinks conflict area between branches as much as possible, more at https://ductile.systems/zdiff3/
- `push.autoSetupRemote` will result in always pushing local branch to remote branch with same name
- `init.defaultBranch main` apparently `master` is called `main`
- `rerere.enabled true` reuse recovered resolution, remembers how merge conflicts were resolved during `git rebase` and automatically resolves conflicts which were already resolved
- `diff.algorithm histogram` clearer diff, more at https://luppeng.wordpress.com/2020/10/10/when-to-use-each-of-the-git-diff-algorithms/
- `includeIf` separate git config for personal and work, useful for setting up different username/email
- `core.autocrlf false` good default on windows, though some people prefer `input` due to some windows tools still not handling `lf` correctly
- `core.editor` set preferred editor