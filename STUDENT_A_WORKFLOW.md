# Student A — Exercise workflow

## Current state and honest evidence

The public repository already contained `index.html`, `style.css`, and `README.md` on `main`, with `dev` at the same initial commit. Student B already pushed `feature/services-footer`. Existing history is preserved.

The header/hero contribution is developed on `feature/header-hero` from `dev`. Its PR must target `dev` and be reviewed and merged by Student B. The website existed before this feature; this PR records improvements to Student A's assigned sections, not a claim that they were first created here.

Repository creation and development-branch setup are already present remotely. Opening VS Code, cloning/pulling on each student's own computer, accepting collaborator invitations, and explaining commands still require the students themselves. A commit author name alone does not verify a GitHub username or collaborator invitation.

## 1. Synchronize your own computer

Run in a terminal. If you already cloned the project, skip the clone and enter its folder.

```bash
git clone https://github.com/abdallahhoueidi/software-company.git
cd software-company
code .
git fetch origin
git branch -a
git switch --track origin/dev
git pull --ff-only origin dev
git switch --track origin/feature/header-hero
```

For branches already present locally, replace `git switch --track origin/NAME` with `git switch NAME`. Do not run these commands over uncommitted work; inspect `git status` first.

In GitHub Settings → Collaborators, verify Student B has accepted access. Invite their verified GitHub account if needed. Do not guess an account from a commit email.

## 2. Header/hero PR handoff

1. Open the PR from `feature/header-hero` into `dev`.
2. Student B checks desktop/mobile layout, keyboard navigation, and the diff.
3. Student B submits a real review from their own account and merges the PR.
4. Keep the branch for evaluation.
5. Student B opens their own `feature/services-footer` → `dev` PR.
6. Student A reviews the actual diff and previews the combined website. Approve only after issues and conflicts are fixed, then merge using a merge commit to preserve branch history.

B's existing branch also reformats parts of the header and hero. If Git reports integration conflicts, preserve Student A's header/hero improvements and Student B's services/footer changes. Student B resolves and pushes conflicts in their own branch before Student A merges. Do not replace the whole file with one side.

After both merges:

```bash
git switch dev
git pull --ff-only origin dev
```

## 3. Challenge A — Update the heading

Start only after both feature PRs have merged into `dev`.

```bash
git switch dev
git pull --ff-only origin dev
git switch -c feature/update-heading
```

In `index.html`, replace the entire `h1` line with:

```html
        <h1 id="hero-title">Your vision.<br>Our expertise.<br><em>Software that matters.</em></h1>
```

```bash
git diff
git add index.html
git commit -m "Update hero heading to emphasize client vision"
git push -u origin feature/update-heading
```

Create a PR: base `dev`, compare `feature/update-heading`. Student B reviews and merges it. Both students pull the updated `dev` before the next challenge.

## 4. Challenge B — Create a real merge conflict

Both students must branch from the SAME latest `dev` before either heading PR merges. Do not create B's branch after A's merge, or the intended conflict will not be demonstrated.

Student A:

```bash
git switch dev
git pull --ff-only origin dev
git rev-parse HEAD
git switch -c feature/heading-a
```

Student B independently pulls `dev`, verifies the same starting SHA, and creates `feature/heading-b`. Agree that the final resolved heading will be `Your vision. Our expertise. Software that matters.`

Student A replaces the same complete `h1` line with:

```html
        <h1 id="hero-title">Bold ideas.<br>Built together.<br><em>Lasting impact.</em></h1>
```

Student B uses different text on that SAME line in their branch, for example:

```html
        <h1 id="hero-title">Smart solutions.<br>Human focus.<br><em>Built for growth.</em></h1>
```

Student A then runs:

```bash
git add index.html
git commit -m "Propose collaborative hero heading for conflict exercise"
git push -u origin feature/heading-a
```

1. A opens `feature/heading-a` → `dev` PR.
2. B reviews and merges A's PR.
3. B opens `feature/heading-b` → `dev` PR; GitHub should report the same-line conflict.
4. B fetches, switches to their branch, and merges `origin/dev`. B edits `index.html`, removes all conflict markers, keeps the agreed final heading, stages, commits, and pushes the resolution.
5. A reviews the resolved diff and approves/merges B's PR into `dev`.
6. Both pull `dev` and verify the website.

Why the conflict happens: both branches changed the same line from the same ancestor. Git cannot choose which text represents the team's intent. A person must choose the agreed result and commit that resolution. Do not manufacture reviews or commits under the other student's identity.

## 5. Final PR and submission

After both features and BOTH heading challenges are merged:

```bash
git switch dev
git pull --ff-only origin dev
git log --oneline --graph --decorate --all
```

Preview the complete site, confirm both names in README, and create `dev` → `main` PR. Review it together, then merge. Both students run:

```bash
git switch main
git pull --ff-only origin main
```

Submit:

- Public repository: https://github.com/abdallahhoueidi/software-company
- README with description, both names, and working run instructions.
- PR links showing each student's authorship and teammate reviews.
- Branch list showing `main`, `dev`, and both students' feature/challenge branches.
- Conflict PR and its resolution commit, with the branch graph as supporting evidence.

## Commands you must be able to explain

| Command | Purpose |
| --- | --- |
| `git init` | Initialize a new local Git repository; unnecessary inside an existing clone. |
| `git remote add origin URL` | Connect a newly initialized repository to GitHub; clone already sets this. |
| `git clone URL` | Copy the remote repository and its history locally. |
| `git status` | Show the current branch and staged/unstaged changes. |
| `git fetch origin` | Download remote refs/history without changing current working files. |
| `git switch -c NAME` | Create and switch to a local branch at the current commit. |
| `git switch --track origin/NAME` | Create a local branch tracking an existing remote branch. |
| `git diff` | Inspect unstaged edits before committing. |
| `git add FILE` | Stage a file's changes for the next commit. |
| `git commit -m MESSAGE` | Record staged changes in local history. |
| `git push -u origin NAME` | Publish a branch and set its upstream. |
| `git pull --ff-only origin dev` | Fetch and update without silently creating a merge commit; stops if histories diverge. |
| `git merge origin/dev` | Integrate current remote dev into the checked-out feature branch; may expose conflicts. |
| `git log --oneline --graph --decorate --all` | Inspect the branch and merge history. |

A pull request is a GitHub review/merge proposal. It is not the same as `git pull`, and pushing a branch does not automatically open a PR.
