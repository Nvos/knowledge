---
tags:
  - git
  - workflow
---

1. Create branch out from `develop` , in case when working with tools such at `gitlab` prefer to create issue and open PR from UI which will create branch
2. Work on new branch, commit often commit names do not matter much now until some break points where it is reasonable to make proper one (most of time it would be 1). When need to commit temporary work just make `WIP` commit and possibly add some annotation to skip CI such as `[skip ci]` on Gitlab
3. Combine all temporary commits into single proper commit via `git reset --soft HEAD@{n}` where `n` is number of latest commits which have to be reverted then just create single commit and push with `--force-with-lease` 
4. In case when there are conflicts with current branch and `develop` then do `git pull develop --rebase` 
5. Then during rebase depending on size of changes either do `--amend` or additional proper commit