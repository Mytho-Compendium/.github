# Git Branching Strategy

This project uses **Git Flow** as its branching strategy across all four repositories: **mytho-compendium-app**, **mytho-compendium-server**, **mytho-compendium-content**, and **.github**.

## Branch Structure

### Permanent Branches

**main**
- Production-ready code only
- Every commit represents a release
- Protected: requires PR reviews and passing CI checks
- Tagged with version numbers (e.g. v1.0.0, v1.1.0)

**develop**
- Integration branch for ongoing development
- Features merge here first
- Should always be in a working state
- Protected: requires PR reviews

### Temporary Branches

**feat/*** (e.g. **feat/GCR-42-android-login-screen**)
- Branch from: **develop**
- Merge to: **develop**
- Purpose: new features or enhancements
- Deleted after merge

**fix/*** (e.g. **fix/GCR-89-android-crash-on-launch**)
- Branch from: **develop** (or **main** for hotfixes)
- Merge to: **develop** (or **main** for hotfixes)
- Purpose: bug fixes
- Deleted after merge

**release/*** (e.g. **release/v1.2.0**)
- Branch from: **develop**
- Merge to: **main** and **develop**
- Purpose: prepare for production release (version bump, final testing, minor fixes)
- Deleted after merge

**hotfix/*** (e.g. **hotfix/GCR-156-android-critical-crash**)
- Branch from: **main**
- Merge to: **main** and **develop**
- Purpose: urgent production fixes
- Deleted after merge

## Workflow

### Standard Feature Development

```bash
# 1. Create feature branch from develop
git checkout develop
git pull origin develop
git checkout -b feat/GCR-42-android-login-screen

# 2. Work on feature, commit changes
git add .
git commit -m "[GCR-42][ANDROID] feat: Add login screen UI"
git push -u origin feat/GCR-42-android-login-screen

# 3. Create PR to develop on GitHub
# 4. After review and approval, merge to develop
# 5. Delete feature branch
```

### Release Preparation

```bash
# 1. Create release branch from develop
git checkout develop
git pull origin develop
git checkout -b release/v1.2.0

# 2. Bump version, update changelog, final testing
git commit -m "[GCR-XXX][BUILD] chore: Bump version to 1.2.0"
git push -u origin release/v1.2.0

# 3. Create PR to main
# 4. After merge to main, tag the release
git checkout main
git pull origin main
git tag -a v1.2.0 -m "Release version 1.2.0"
git push origin v1.2.0

# 5. Merge release branch back to develop
git checkout develop
git merge release/v1.2.0
git push origin develop

# 6. Delete release branch
```

### Hotfix for Production

```bash
# 1. Create hotfix branch from main
git checkout main
git pull origin main
git checkout -b hotfix/GCR-156-android-critical-crash

# 2. Fix the issue
git commit -m "[GCR-156][ANDROID] fix: Resolve critical crash on startup"
git push -u origin hotfix/GCR-156-android-critical-crash

# 3. Create PR to main
# 4. After merge to main, tag the hotfix
git checkout main
git pull origin main
git tag -a v1.2.1 -m "Hotfix version 1.2.1"
git push origin v1.2.1

# 5. Merge hotfix back to develop
git checkout develop
git merge hotfix/GCR-156-android-critical-crash
git push origin develop

# 6. Delete hotfix branch
```

## Version Tagging

All releases on **main** must be tagged with semantic versioning:
- **Major** (v2.0.0): breaking changes
- **Minor** (v1.2.0): new features, backward compatible
- **Patch** (v1.2.1): bug fixes only

Tags should match the **versionName** in **build.gradle** (Android) or the equivalent in the server and content repos.

## Branch Protection (GitHub Rulesets)

Both **main** and **develop** are protected by an active GitHub Ruleset in all four repositories (**mytho-compendium-app**, **mytho-compendium-server**, **mytho-compendium-content**, **.github**). The ruleset configuration is strictly identical across all branches and all repos:

- **Branch deletion blocked**: neither **main** nor **develop** can be deleted
- **Force pushes blocked**: non-fast-forward commits are rejected
- **Pull Request required**: no direct commits allowed, all changes must go through a PR
  - **Code owner review required**: the **CODEOWNERS** file governs who must approve
  - **All review threads must be resolved**: no open comments can remain before merging
  - **Rebase only**: merge commits and squash merges are disabled, only rebase is allowed
  - **0 required approvals**: solo project, the code owner review is the sole gate
- **No bypass**: no actor can bypass these rules, not even repository admins

## Why Git Flow?

This strategy was chosen for:
- **Clear separation**: development vs production code is explicit
- **Release management**: structured approach to versioning and deployment
- **Experimentation safety**: features can be developed in isolation without affecting production
