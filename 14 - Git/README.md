# Git and Version Control

**Priority:** Medium · **Prerequisite:** [[13 - Testing and Debugging/README|Testing]] · **Related:** [[15 - Cloud and Deployment/README|Cloud]]

## Git model

Git records snapshots rather than treating a project as only a sequence of file differences. The working tree contains edits, the index/staging area selects content for the next commit, and the repository stores commits and references. A branch is a movable reference to commits.

## Commands and meanings

`git status` inspects state. `git diff` shows unstaged differences. `git diff --staged` shows staged differences. `git add` stages. `git commit` creates a snapshot. `git log` inspects history. `git fetch` downloads remote history. `git pull` fetches and integrates. `git push` publishes commits. `git switch -c feature/name` creates and switches branches.

## Merge, rebase, reset

Merge creates a merge result and preserves branch history. Rebase replays commits on a new base and creates new commit identities; do not rewrite shared history casually. `reset` moves references and may alter staging/working state; `revert` creates a new commit that undoes an earlier commit and is safer for published history.

## Conflicts and collaboration

A conflict means Git cannot combine changes automatically. Read both versions, create the correct result, remove markers, run tests, stage, and commit. Pull requests should contain focused changes, context, tests, and migration/security notes when relevant.

## Safety

Use `.gitignore` for generated files and local configuration. Secrets do not become safe merely because a file is ignored after being committed; rotate exposed credentials and remove them from history when needed. Tags can identify releases.

## Checklist

- [ ] Working tree, index, repository, branch
- [ ] status, diff, add, commit, log
- [ ] fetch, pull, push, clone
- [ ] Merge versus rebase
- [ ] Reset versus revert
- [ ] Conflict resolution
- [ ] Pull requests and commit quality
- [ ] `.gitignore` and secret leakage
