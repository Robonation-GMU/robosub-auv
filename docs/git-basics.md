# Git and GitHub basics (Windows, sorry I don't have Linux setup rn!)

A step-by-step guide to putting files on GitHub yourself.

## The three ideas you need

- **Git** is a program on your laptop that tracks changes to files in a folder. That folder is called a **repository** (repo).
- **GitHub** is a website that stores a copy of your repo online so the team can share it.
- You make changes on your laptop, save them as a **commit** (a snapshot with a message), then **push** them to GitHub. Teammates **pull** to get your changes.

```
your files → git add → git commit → git push → GitHub
```

## One-time setup

### 1. Get access
Make a free GitHub account (any email) and send your username to a team lead, who will add you to the **Robonation-GMU** organization. Accept the email invite.

### 2. Install Git
Download from https://git-scm.com/download/win and install with the default options. This also installs **Git Bash**, a terminal you can use for every command below (PowerShell works too).

> Pasting in Git Bash: use **right-click → Paste** or **Shift+Insert**. Ctrl+V can sneak in a hidden character and cause `fatal: protocol 'https' is not supported`.

### 3. Tell Git who you are
Open Git Bash and run, with your own name and the email on your GitHub account (keep the quotes):
```
git config --global user.name "First Last"
git config --global user.email "you@example.com"
```
This labels your commits. 

### 4. Download the repo (clone)
```
cd ~/Documents
git clone https://github.com/Robonation-GMU/robosub-auv.git
cd robosub-auv
```
You now have the whole repo as a folder on your laptop. The first time you push, a browser window asks you to sign in to GitHub.

## Typical workflow after that

```
git checkout main
git pull                                  # get teammates' latest work
git checkout -b yourname/zed-camera-test    # make your own branch
# ...edit or add files...
git add .
git commit -m "Add ZED frame grab script"
git push -u origin yourname/zed-camera-test
```

What each line does:

| Command | What it means |
|---------|---------------|
| `git checkout main` | Switch to the `main` branch, the team's shared, working version. You start new work from here. |
| `git pull` | Download the newest changes from GitHub so you aren't building on an old copy. |
| `git checkout -b yourname/zed-camera-test` | Create a new branch and switch to it (`-b` means "make a new branch"). This is your own copy of the repo, so your changes don't touch `main`. Name it `yourname/what-you-are-doing`. |
| *edit or add files* | Work normally in the folder: write code, add notes. |
| `git add .` | Choose which changes go into your next save. The `.` means everything in this folder. |
| `git commit -m "..."` | Save a snapshot of those changes on your laptop. `-m` adds a message describing what you did. Nothing is online yet. |
| `git push -u origin yourname/zed-camera-test` | Upload your branch to GitHub. `origin` is the nickname for the GitHub repo, and `-u` remembers the link so next time plain `git push` works. |

Then on github.com, click **Compare & pull request**, ask a teammate to review, and merge it.

## Switching branches

You only use `-b` once, when you first **create** a branch. To move between branches that already exist, leave it off:
```
git checkout -b yourname/zed-notes   # first time: create it and switch to it
git checkout main                    # switch back to main
git checkout yourname/zed-notes      # back to your existing branch (no -b)
```
- If Git says `a branch named '...' already exists`, drop the `-b`.
- When you switch to `main`, files from your branch seem to disappear. They're safe on your branch and come back when you switch to it.
- Once a branch is pushed with `-u`, later pushes from it are just `git push`.

## Adding specific files

`git add .` adds everything. To pick files, put their paths after `git add` instead of the dot. Paths start from the folder you're in (usually the repo's top folder):
```
git add README.md                                   # one file
git add docs/git-basics.md docs/hardware/zed2i.md   # several files, separated by spaces
git add docs/hardware/                              # everything inside one folder
```
- Run `git status` first. It lists changed files with their exact paths.
- Press **Tab** while typing a path and Git Bash fills in the rest.
- Added something by mistake? `git restore --staged <file>` takes it back out. Your file isn't changed.
- Run `git status` again before committing: green files go in, red ones don't.

## Common errors

| What you see | What it means and how to fix it |
|--------------|---------------------------------|
| `fatal: protocol 'https' is not supported` | A hidden character got pasted before `https`. Retype `https://` by hand, and paste with right-click or Shift+Insert, not Ctrl+V. |
| `error: pathspec '...' did not match any file(s)` on commit | You forgot `-m`. Use `git commit -m "your message"`. |
| `! [rejected] ... (fetch first)` on push | GitHub has changes you don't have yet. Run `git pull --no-rebase`, then `git push`. |

## Useful commands

| Command | What it does |
|---------|--------------|
| `git status` | What changed and what's staged |
| `git log --oneline` | List of past commits |
| `git diff` | Exact line changes you haven't staged |
| `git branch` | Which branch you're on |
| `git checkout <branch>` | Switch branches |
| `git pull` | Download new commits from GitHub |
