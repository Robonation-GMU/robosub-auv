# Git and GitHub basics (Windows)

A step-by-step guide to putting files on GitHub yourself.

## The three ideas you need

- **Git** is a program on your laptop that tracks changes to files in a folder. That folder is called a **repository** (repo).
- **GitHub** is a website that stores a copy of your repo online so the team can share it.
- You make changes on your laptop, save them as a **commit** (a snapshot with a message), then **push** them to GitHub. Teammates **pull** to get your changes.

```
your files → git add → git commit → git push → GitHub
```

## One-time setup (every member)

### 1. Get access
Make a free GitHub account and send your username to a team lead, who will add you to the **Robonation-GMU** organization. Accept the email invite.

### 2. Install Git
Download from https://git-scm.com/download/win and install with the default options. This also installs **Git Bash**, a terminal you can use for every command below (PowerShell works too).

> Pasting in Git Bash: use **right-click → Paste** or **Shift+Insert**. Ctrl+V can sneak in a hidden character and cause `fatal: protocol 'https' is not supported`.

### 3. Tell Git who you are
Open Git Bash and run, with your own name and the email on your GitHub account (keep the quotes):
```
git config --global user.name "First Last"
git config --global user.email "you@example.com"
```
This only labels your commits. It is not a login.

### 4. Download the repo (clone)
```
cd ~/Documents
git clone https://github.com/Robonation-GMU/robosub-auv.git
cd robosub-auv
```
You now have the whole repo as a folder on your laptop. The first time you push, a browser window asks you to sign in to GitHub.

## Everyday workflow after that

```
git checkout main
git pull                                  # get teammates' latest work
git checkout -b yourname/zed-camera-test    # make your own branch
# ...edit or add files...
git add .
git commit -m "Add ZED frame grab script"
git push -u origin yourname/zed-camera-test
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
