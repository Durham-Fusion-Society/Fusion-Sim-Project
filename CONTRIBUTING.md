# Contributing

Hello everyone, below is a comprehensive guide on how to get started with
contributing to the project.
You don't need any git experience to contribute. This guide walks you
through everything, it may seem complicated at first, but stick with it. 
Being able to contribute to large projects is a very useful (and impressive on 
your CV) skill.

## How this project works

Nobody except the maintainers can change the main repository directly. Instead,
everyone, including regulars, follows the same loop:

```
main repo  ->  your fork  ->  your edit  ->  pull request  ->  review  ->  merged
(read-only)    (your copy)    (you change    (you ask us to
                               your copy)     take the change)
```

- **Fork:** your own personal copy of the project on GitHub. You can break it
  freely; it can't affect anyone else.
- **Pull request (PR):** a request that says "pput my changes into the
  main project". A maintainer reviews it, then merges it.


## What to work on

1. Open [LEDGER.md](LEDGER.md). 
2. Pick an unclaimed item.
3. Claim it by opening a PR that changes its status to `in progress` with your
   GitHub username. (Small, a good first PR.)



##How to Contribute

## Route A: do everything in the browser 

Best for documentation fixes, ledger updates.

### 1. Fork the repository

1. Go to the project's GitHub page.
2. Click **Fork** (top right), then **Create fork**.
3. You're now on **your** copy at `github.com/<your-username>/<repo-name>`.

### 2. Make your edit

1. In your fork, click the file you want to change.
2. Click the **pencil icon** (Edit this file).
3. Make your change.
4. Click **Commit changes...** (top right).
5. Write a short message saying what you did (see
   [Writing a good commit message](#writing-a-good-commit-message)).
6. Choose **Create a new branch for this commit and start a pull request**. Give
   the branch a short name, e.g. `add-rk4-step`.
7. Click **Propose changes**.

### 3. Open the pull request

1. On the page that appears, check the title and description. The
   [checklist below](#before-you-open-a-pull-request) helps.
2. Click **Create pull request**.

Done! A maintainer will look at it. Skip to
[After you submit](#after-you-submit).

---

## Route B: edit on your own computer

Use this when you want to **run** the code, change several files, or test your
work. You'll use the command line (Terminal on Mac/Linux, Git Bash on Windows)
or [GitHub Desktop](https://desktop.github.com), which does the same steps
with buttons.

### One-time setup

1. [Install git](https://git-scm.com/downloads).
2. Tell git who you are (use the email on your GitHub account):

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "you@example.com"
   ```

### 1. Fork, then clone your fork

Fork on GitHub exactly as in Route A step 1. Then, on your fork's page, click
the green **Code** button, copy the HTTPS link, and run:

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```

"Clone" means "download a copy to my computer".

### 2. Link to the original project (once)

This lets you pick up other people's changes later:

```bash
git remote add upstream https://github.com/mattmiester/gyromotion-sim.git
```

### 3. Make a branch for your change

Always work on a new branch, never directly on `main`:

```bash
git switch -c add-rk4-step
```

Pick a short name that describes the change, using lowercase and dashes.

### 4. Edit, then check what you changed

Edit files in any editor (Spyder, VS Code, Notepad). Then:

```bash
git status      # which files did I change?
git diff        # exactly what changed, line by line
```

If it's code, run it first and make sure it works.

### 5. Save your work (commit)

```bash
git add path/to/changed_file.py
git commit -m "Add RK4 step function"
```

`git add` picks which changes to include. `git commit` saves them with a
message. Add only the files you meant to change.

### 6. Send it to your fork (push)

```bash
git push -u origin add-rk4-step
```

The first time, GitHub may ask you to sign in. Use your browser login, or a
[personal access token](https://github.com/settings/tokens) if it asks for a
password; your normal password won't work on the command line.

### 7. Open the pull request

Go to your fork on GitHub. A yellow banner says **Compare & pull request**:
click it, fill in the details, then **Create pull request**.

---

### Writing a good PR description

```
Who:

What: Added rk4_step() with the same (x, v, dt) -> (x, v) signature as euler_step.
Why:  Needed for the Euler vs RK4 comparison.
How I checked: ran gyromotion.py; radius error stays under 1e-3 after 10 orbits at N=100.
```


## Keeping your fork up to date

Before starting new work, pull in the latest from the main project.

**Browser:** on your fork, click **Sync fork**, then **Update branch**.

**Computer:**

```bash
git switch main
git fetch upstream
git merge upstream/main
git push origin main
```

Then make a **new** branch for your next change.

## If something goes wrong

| Problem | What to do |
|---|---|
| "Permission denied" when pushing | You cloned the main repo, not your fork. Fork, then clone **your fork's** link (Route B step 1). |
| I edited `main` by mistake | Don't panic. Run `git switch -c my-new-branch` to move your changes to a new branch, then continue. |
| The PR says there are conflicts | Someone changed the same lines. Sync your fork (above), then ask in the PR if you're stuck. Maintainers will help. |
| I committed a file I shouldn't have | Tell us in the PR, or ask how to remove it. We'll sort it out. |
| I'm lost | Open an Issue or comment on your PR. Asking is always fine. |


