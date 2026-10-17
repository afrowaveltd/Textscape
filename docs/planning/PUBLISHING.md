# Publishing this initial draft to GitHub

This Git repository is prepared locally, **but has not yet been published**. It was drafted for the `afrowaveltd` GitHub account. The repository does not yet exist there as of the initial check on 2026-10-17.

## Create the public repository

1. Sign in to GitHub as `afrowaveltd`.
2. Open https://github.com/new.
3. Set **Owner** to `afrowaveltd`, **Repository name** to `Textscape` and **Visibility** to **Public**.
4. Description suggestion: `Initial concept for a transparent, terminal-native web browser and personal information workspace.`
5. **Do not initialize with README, .gitignore or a license**: these are either already part of the local seed or intentionally undecided.
6. Create the repository.

## Publish the prepared local Git commit

Download and unpack the Textscape repository archive supplied with this project. The archive intentionally includes the `.git` directory and initial commit.

Run from inside the extracted `Textscape` directory:

```bash
git status
git remote add origin https://github.com/afrowaveltd/Textscape.git
git push -u origin main
```

GitHub may request authentication with a credential helper, personal access token or SSH; do not store credentials inside project files.

If you prefer SSH:

```bash
git remote add origin git@github.com:afrowaveltd/Textscape.git
git push -u origin main
```

Use one remote method, not both. On success, the project should be available at `https://github.com/afrowaveltd/Textscape`.

## After publishing

- Verify visibility says **Public** and README opens.
- Choose a suitable license deliberately and add `LICENSE`. **Public does not automatically mean open-source licensed.** OSI-approved open-source licensing and civil-only-use restrictions are incompatible requirements and need an explicit decision.
- Choose repository topics (suggestions: `rust`, `terminal`, `tui`, `browser`, `email`, `automation`, `privacy`, `ai`, `concept`). These are suggestions rather than current feature claims.
- Open design issues from ROADMAP/OPEN-QUESTIONS and enable branch protection/tests when implementation begins.
- Avoid publishing real browsing data, cookies, private email, API credentials or unreleased third-party content in public issues.

The initial commit contains **documentation and design intentions only**. No code, tests, binaries or product releases exist yet.
