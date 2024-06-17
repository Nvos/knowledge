# Revert commit amends

1. Use `git reflog` in order to find specific `HEAD@{n}`
2. Do git `reset --soft HEAD@{n}`

# Revert nested merge commit

1. Create temporary branch from branch containing nested merge commit at point before merge commit - `git checkout -b temp merge-commit-hash^` . `^` at the end means one revision behind, can be used multiple times
2. Rebase `temp` branch onto develop - `git rebase develop`
3. Rebase remaining commits after merge commit onto `temp` branch

# Update existing tag

1. Find commit id to which tag should be changed via `git log`
2. Update locally with force `git tag --force {tag name} {commit id}`
3. Push tag with force `git push --force --tags`
4. Sync local tags with remote `git fetch --prune --prune-tags`
