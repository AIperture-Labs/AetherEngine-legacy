# Repository workflow

Branches, worktrees, commits, pull requests, releases and tracking.
Read this before any git, branch, commit, PR or issue operation.

## Branches

- `main` — the default branch, protected: no deletion, no force push,
  changes only through a pull request. Never commit directly on `main`.
- Feature and fix branches — one per change, created from `main`, named
  `<type>/<short-description>` where `<type>` is a Conventional Commits type:
  `feat/`, `fix/`, `docs/`, `refactor/`, `perf/`, `test/`, `build/`, `ci/`,
  `chore/`, `style/`, `revert/` (e.g. `feat/vulkan-swapchain`).
- Never enable automatic deletion of merged branches on the remote. Never
  delete a branch, locally or on the remote, without asking the user first.
  `main` is permanent.

## Worktrees

All work happens in worktrees under `.worktrees/`, ignored by git, one per
branch. Name each worktree after its branch, so the path carries the
Conventional Commits type. Create it from `main`; once the branch is merged
and the user agrees, remove the worktree and its branch:

```sh
git worktree add -b feat/my-new-feature .worktrees/feat/my-new-feature main
git worktree remove .worktrees/feat/my-new-feature
git branch -d feat/my-new-feature
```

A worktree containing submodules cannot be moved with `git worktree move`:
move the directory, then run `git worktree repair`.

## GitHub protections

Settings that enforce the rules above; check them with
`gh api repos/{owner}/{repo}/rulesets`. Change them only when the user asks.

- Repository: squash merge only (merge commit and rebase disabled), no
  automatic deletion of merged branches.
- Ruleset `main`, active, on the default branch, no bypass actor: deletion
  blocked, force push blocked, linear history required, changes through a pull
  request (squash only, 0 approving reviews while there is a single
  maintainer).
- Not yet enforced: required status checks (no CI yet) and required reviews.

## Commits

- Follow Conventional Commits:
  <https://www.conventionalcommits.org/en/v1.0.0/>. Read that spec when in
  doubt. Format: `type(scope): description`, with `!` after the type or
  scope, or a `BREAKING CHANGE:` footer, for a breaking change. The scope is
  the area touched (`cmake`, `core`, `deps`, `agents`, `readme`…).
- Keep commits small and atomic: one coherent change, no unrelated work
  mixed in.
- Commit a step only after the user has reviewed it.
- An agent may co-sign its commits and PRs with its own name and the model
  used, e.g. `Co-Authored-By: <agent> <model> <<email>>` as a commit trailer
  or at the end of a PR description. If the user opposes it, don't.

## Pull requests

- Branch → `main`, merged with a squash merge. The PR title follows
  Conventional Commits: the squash keeps it as the commit message.
- Parked in-progress code (an experiment that doesn't work yet but is worth
  keeping) lives in a draft PR, with notes and findings in its description —
  not in a separate Markdown write-up.

## Releases

Releases are tagged by hand as semver `vX.Y.Z`, on the merge commit of a
`chore(release): vX.Y.Z` PR that bumps the project version in
`CMakeLists.txt`, once CI is green. Never tag unless the user asks.

## Tracking

Work is tracked with GitHub issues, and the roadmap with a GitHub Project.
Each issue states its goal and how to verify it; branches and PRs reference
it.
