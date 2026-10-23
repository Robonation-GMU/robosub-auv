# Git and GitHub basics (Windows)

A step-by-step guide to putting files on GitHub yourself.

## The three ideas you need

- **Git** is a program on your laptop that tracks changes to files in a folder. That folder is called a **repository** (repo).
- **GitHub** is a website that stores a copy of your repo online so the team can share it.
- You make changes on your laptop, save them as a **commit** (a snapshot with a message), then **push** them to GitHub. Teammates **pull** to get your changes.

```
your files → git add → git commit → git push → GitHub
```

## One-time setup

### 1. Install Git
Download from https://git-scm.com/download/win and install with the default options. This also installs **Git Bash**, a terminal you can use for every command below (PowerShell works too).

### 2. Tell Git who you are
Open Git Bash and run (use the email on your GitHub account):
```
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### 3. Create the empty repo on GitHub
On github.com click **New repository**, name it (e.g. `robosub-auv`), and leave README, .gitignore and license **unchecked**. Click **Create**. Copy the URL it shows, like `https://github.com/gmu-robosub/robosub-auv.git`.

## Put the starter files on GitHub

### 4. Download the repo to your laptop (clone)
```
cd ~/Documents
git clone https://github.com/gmu-robosub/robosub-auv.git
cd robosub-auv
```
Git may warn that you cloned an empty repository. That's expected.

### 5. Copy the files in
Unzip the starter files and copy everything inside `robosub-starter/` into your `robosub-auv` folder. Include the hidden ones: `.gitignore` and the `.github` folder. (In File Explorer: View → Show → Hidden items.)

### 6. See what Git noticed
```
git status
```
Files in red are new or changed but not yet staged.

### 7. Stage the files (choose what goes in the snapshot)
```
git add .
```
The `.` means "everything in this folder." Run `git status` again and they turn green.

### 8. Commit (take the snapshot)
```
git commit -m "Add starter folder structure and docs"
```

### 9. Push to GitHub
```
git branch -M main
git push -u origin main
```
The first time, a browser window opens asking you to sign in to GitHub. After that, refresh the repo page on github.com and your files are there.

## Everyday workflow after that

```
git checkout main
git pull                                  # get teammates' latest work
git checkout -b sneaks/zed-camera-test    # make your own branch
# ...edit or add files...
git add .
git commit -m "Add ZED frame grab script"
git push -u origin sneaks/zed-camera-test
```
Then on github.com, click **Compare & pull request**, ask a teammate to review, and merge it.

## Handy commands

| Command | What it does |
|---------|--------------|
| `git status` | What changed and what's staged |
| `git log --oneline` | List of past commits |
| `git diff` | Exact line changes you haven't staged |
| `git branch` | Which branch you're on |
| `git checkout <branch>` | Switch branches |
| `git pull` | Download new commits from GitHub |

## If you prefer clicking

**GitHub Desktop** (https://desktop.github.com) does all of the above with buttons. It's fine to start there, but learning the commands pays off on the Jetson, which has no GitHub Desktop.
