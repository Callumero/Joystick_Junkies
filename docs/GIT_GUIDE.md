# Git Guide for Complete Beginners

This guide will teach you everything you need to know about Git and GitHub Desktop for the game jam. No prior experience required!

## Table of Contents

1. [What is Git and Why Use It?](#what-is-git-and-why-use-it)
2. [Installing GitHub Desktop (Windows)](#installing-github-desktop-windows)
3. [Creating a GitHub Account](#creating-a-github-account)
4. [Forking This Template](#forking-this-template)
5. [Adding Your Team as Collaborators](#adding-your-team-as-collaborators)
6. [Cloning Your Fork](#cloning-your-fork)
7. [Daily Workflow](#daily-workflow)
8. [Using Branches (Highly Recommended!)](#using-branches-highly-recommended)
9. [Working as a Team](#working-as-a-team)
10. [Emergency Fixes](#emergency-fixes)

---

## What is Git and Why Use It?

Git is a tool that:
- **Saves every version** of your project (like unlimited undo)
- **Lets your whole team work together** without overwriting each other's work
- **Backs up your project** to the cloud (GitHub)
- **Tracks who changed what** so you can see the history

**Without Git:** "final_game_v2_FINAL_actually_final.zip"

**With Git:** A clean history of every change, easy to undo mistakes, and everyone on your team stays in sync.

---

## Installing GitHub Desktop (Windows)

GitHub Desktop is a free app that makes Git easy to use with buttons instead of commands.

### Step 1: Download GitHub Desktop

1. Go to [desktop.github.com](https://desktop.github.com)
2. Click the big **"Download for Windows"** button
3. Wait for the download to complete

### Step 2: Install GitHub Desktop

1. Open the downloaded file (`GitHubDesktopSetup-x64.exe`)
2. The installer runs automatically - just wait
3. GitHub Desktop will open when it's done

### Step 3: Sign In

1. Click **"Sign in to GitHub.com"**
2. This opens your web browser
3. Enter your GitHub username and password
4. Click **"Authorize desktop"**
5. Return to GitHub Desktop - you're now signed in!

---

## Creating a GitHub Account

If you don't have a GitHub account yet:

1. Go to [github.com](https://github.com)
2. Click **"Sign up"** in the top right
3. Enter your email address
4. Create a password
5. Choose a username (this will be public!)
6. Complete the verification puzzle
7. Check your email and click the verification link

**Tip:** Use an email you check regularly - you'll get notifications about your team's work.

---

## Forking This Template

"Forking" creates your own copy of this template that your team can modify.

### Step 1: Fork on GitHub

1. Go to the original template repository on GitHub
2. Click the **"Fork"** button (top right, near "Star")
3. Select your account as the destination
4. Wait for GitHub to create your copy
5. You now have your own repository!

### Step 2: Rename Your Fork (Optional)

1. Go to your new forked repository
2. Click **"Settings"** (tab near the top)
3. Under "Repository name", change it to your game's name
4. Click **"Rename"**

---

## Adding Your Team as Collaborators

So your whole team can push changes:

### Step 1: Go to Repository Settings

1. Go to your forked repository on GitHub
2. Click **"Settings"** (tab near the top)

### Step 2: Add Collaborators

1. Click **"Collaborators"** in the left sidebar
2. Click **"Add people"**
3. Type your teammate's GitHub username or email
4. Click **"Add [username] to this repository"**
5. Repeat for each team member

### Step 3: Teammates Accept the Invitation

Your teammates will receive an email invitation. They need to:
1. Open the email from GitHub
2. Click **"View invitation"**
3. Click **"Accept invitation"**

Now everyone can push to the repository!

---

## Cloning Your Fork

"Cloning" downloads the repository to your computer so you can work on it.

### In GitHub Desktop:

1. Click **"File"** > **"Clone repository..."** (or press Ctrl+Shift+O)
2. Click the **"GitHub.com"** tab
3. Find your forked repository in the list
4. Choose where to save it on your computer (Local path)
5. Click **"Clone"**

Wait for the download to complete. You now have the project on your computer!

**Important:** Remember where you saved it! You'll open this folder in your game engine.

---

## Daily Workflow

Follow this workflow every time you work on the project:

### The Golden Rule: ALWAYS PULL FIRST

Before you start working:

1. Open GitHub Desktop
2. Make sure your repository is selected
3. Click **"Fetch origin"** (top bar)
4. If there are changes, click **"Pull origin"**

This downloads any changes your teammates made. **Do this EVERY time you start working!**

### Making Changes

1. Open your game engine (Unity/Godot/GameMaker)
2. Make your changes
3. Save your work in the engine

### Seeing Your Changes in GitHub Desktop

GitHub Desktop automatically detects changes:

1. Open GitHub Desktop
2. Look at the left panel - you'll see a list of changed files
3. Changed files have colored icons:
   - **Green (+)** = New file
   - **Yellow (dot)** = Modified file
   - **Red (-)** = Deleted file

### Committing Your Changes

A "commit" is like a save point. Make commits often!

1. In the left panel, check the boxes for files you want to include
2. At the bottom left, find the **"Summary"** field
3. Write a short description of what you changed (e.g., "Add player jump ability")
4. Click **"Commit to main"** (or your branch name)

**Good commit messages:**
- "Add player movement script"
- "Fix bug where enemies spawn twice"
- "Update main menu background"

**Bad commit messages:**
- "stuff"
- "changes"
- "asdfasdf"

### Pushing Your Changes

After committing, your changes are saved locally. To share with your team:

1. Click **"Push origin"** (top bar)
2. Wait for the upload to complete

Your teammates can now pull your changes!

---

## Using Branches (Highly Recommended!)

Branches let you work on features without affecting the main project. **We strongly recommend using branches!**

### Why Use Branches?

- **Safety:** If your experiment breaks things, main is still fine
- **Parallel work:** Everyone can work on different features simultaneously
- **Clean history:** Features are grouped into neat packages

### Creating a Branch in GitHub Desktop

1. Click the **"Current branch"** dropdown (shows "main")
2. Click **"New branch"**
3. Give it a descriptive name like:
   - `feature/player-shooting`
   - `feature/main-menu`
   - `fix/enemy-spawn-bug`
4. Click **"Create branch"**

You're now on your new branch!

### Switching Between Branches

1. Click the **"Current branch"** dropdown
2. Click the branch you want to switch to

**Warning:** Save and commit your work before switching branches!

### When to Create a Branch

Create a new branch when you're:
- Adding a new feature (player abilities, new levels, etc.)
- Trying something experimental
- Working on something that might break other things
- Fixing a specific bug

### Merging Your Branch Back

When your feature is done:

1. Commit and push all your changes
2. Go to your repository on GitHub (in your web browser)
3. You'll see a prompt: **"[your-branch] had recent pushes"**
4. Click **"Compare & pull request"**
5. Add a title and description
6. Click **"Create pull request"**
7. If there are no conflicts, click **"Merge pull request"**
8. Click **"Confirm merge"**

Your changes are now in main!

### Keeping Your Branch Updated

If teammates merged changes to main while you were working:

1. Switch to your branch in GitHub Desktop
2. Click **"Branch"** menu > **"Update from main"**
3. This brings the latest main changes into your branch

Do this regularly to avoid big conflicts later!

---

## Working as a Team

### Communication is Key

- **Tell your team when you push changes** (Discord, group chat, etc.)
- **Tell your team what you're working on** to avoid conflicts
- **Pull before you start working** - always!

### Pull Requests

Pull requests let your team review changes before merging:

1. Push your branch to GitHub
2. On GitHub, click **"Pull requests"** tab
3. Click **"New pull request"**
4. Select your branch
5. Click **"Create pull request"**
6. Your teammates can review and comment
7. When approved, merge it!

### Merge Conflicts

Merge conflicts happen when two people edit the same part of a file.

**When you see a conflict:**

1. GitHub Desktop will show which files have conflicts
2. Click **"Open in [editor]"** to see the conflict
3. Look for these markers:
   ```
   <<<<<<< HEAD
   Your changes
   =======
   Their changes
   >>>>>>> other-branch
   ```
4. Edit the file to keep what you want
5. Remove the conflict markers
6. Save the file
7. In GitHub Desktop, click **"Continue merge"**

**Tip:** Talk to the other person to decide which changes to keep!

### Avoiding Conflicts

- **Use branches** - this keeps work separated
- **Pull often** - the more up-to-date you are, the fewer conflicts
- **Commit small changes frequently** - easier to merge
- **Communicate** - "I'm editing the player script!"

---

## Emergency Fixes

### "I Broke Everything!"

Don't panic! Git has your back.

**To undo uncommitted changes to a file:**

1. In GitHub Desktop, right-click the file
2. Click **"Discard changes"**
3. The file is back to how it was at your last commit

**To undo ALL uncommitted changes:**

1. Click **"Repository"** menu
2. Click **"Discard all changes..."**
3. Click **"Discard changes"**

### "I Want to Go Back to an Earlier Version"

1. Click **"History"** tab in GitHub Desktop
2. Find the commit you want to go back to
3. Right-click it
4. Click **"Revert changes in commit"**

This creates a new commit that undoes those changes.

### "I Committed to the Wrong Branch!"

1. Note down what your commit was (look in History)
2. Switch to the correct branch
3. Click **"Branch"** > **"Cherry-pick commit..."**
4. Select the commit you want to bring over

### "My Teammate and I Both Worked on the Same File"

This is a merge conflict. See the [Merge Conflicts](#merge-conflicts) section above.

### "GitHub Desktop Shows Weird Errors"

Try these in order:

1. **Fetch and pull** - Click "Fetch origin", then "Pull origin"
2. **Restart GitHub Desktop** - Close and reopen the app
3. **Check your internet** - Git needs internet to sync
4. **Ask for help** - Some errors need an experienced person

---

## Quick Reference

### Daily Checklist

1. [ ] Open GitHub Desktop
2. [ ] Fetch origin
3. [ ] Pull if there are changes
4. [ ] Do your work
5. [ ] Commit with a good message
6. [ ] Push origin

### GitHub Desktop Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Clone repository | Ctrl+Shift+O |
| Commit | Ctrl+Enter |
| Push | Ctrl+P |
| Pull | Ctrl+Shift+P |
| New branch | Ctrl+Shift+N |
| Switch branch | Ctrl+B |

### Command Line (Optional)

If you want to use the command line instead:

```bash
git pull                     # Download changes
git add .                    # Stage all changes
git commit -m "Your message" # Commit changes
git push                     # Upload changes
git checkout -b branch-name  # Create new branch
git checkout main            # Switch to main
git merge branch-name        # Merge branch
```

---

## Need More Help?

- [GitHub Desktop Documentation](https://docs.github.com/en/desktop)
- [Git Basics Video Tutorial](https://www.youtube.com/results?search_query=git+basics+for+beginners)
- Ask your teammates!
- Ask the jam organizers!

**Remember:** Everyone was a beginner once. Don't be afraid to ask questions!
