# Releasing Your Game on GitHub

When the jam ends, you'll submit your game by creating a GitHub Release. This guide walks you through the entire process.

---

## Overview

A GitHub Release is:
- A snapshot of your project at a specific point
- A place to attach downloadable files (your game build)
- A public page with a description and changelog
- The link you'll submit to the jam

---

## Step 1: Build Your Game

First, export your game from your engine.

### GameMaker

1. Go to **Build > Create Executable**
2. Select **Package as ZIP** (recommended) or just the executable
3. Choose **Windows** as the target
4. Pick a location **outside** your project folder
5. Click **Save** and wait for the build

Your output will be a `.zip` file or a folder containing:
- `YourGame.exe`
- `data.win`
- Any included files

### Godot

1. Go to **Project > Export**
2. If you haven't set up exports yet:
   - Click **Add...**
   - Select **Windows Desktop**
   - Download export templates if prompted
3. Click **Export Project**
4. Choose a location **outside** your project folder
5. Name it `YourGame.exe`
6. Click **Save**

Your output folder will contain:
- `YourGame.exe`
- `YourGame.pck`

### Unity

1. Go to **File > Build Settings**
2. Make sure your scenes are added to **Scenes In Build**
3. Select **Windows** as the platform
4. Click **Build**
5. Choose a location **outside** your project folder
6. Wait for the build to complete

Your output folder will contain:
- `YourGame.exe`
- `YourGame_Data/` folder
- `UnityPlayer.dll`
- Other DLL files

---

## Step 2: Test Your Build

**This step is critical!** Your game might work in the editor but fail as a standalone build.

### Testing Checklist

1. [ ] Copy the entire build folder to a different location (like Desktop)
2. [ ] Run the game from that new location
3. [ ] Test all major features:
   - [ ] Game starts without errors
   - [ ] Main menu works
   - [ ] Gameplay functions
   - [ ] Sound plays
   - [ ] You can quit the game
4. [ ] Test on a different computer if possible

### Common Build Problems

| Problem | Likely Cause |
|---------|--------------|
| Game won't start | Missing DLL files or data files |
| No sound | Audio files not included in build |
| Missing graphics | Assets not in the right folder |
| Crash on start | Hardcoded file paths in your code |

---

## Step 3: Prepare Your Release Files

### Create a ZIP File

1. Put all your build files in a single folder
2. Name the folder something clear (e.g., `MyGame-Windows`)
3. Right-click the folder
4. Select **Send to > Compressed (zipped) folder** (Windows)
   - Or use **Compress** on Mac
5. You should have a file like `MyGame-Windows.zip`

### What to Include

**Must include:**
- The executable (`.exe`)
- All data files and folders
- Any DLLs

**Good to include:**
- `README.md` with:
  - How to play (controls)
  - Credits
  - Known issues

**Don't include:**
- Source code (it's already in your repo)
- Massive files you don't need
- Debug builds

### File Size Tips

GitHub Releases allow files up to **2GB** each, but smaller is better:
- Compress audio (use OGG, not WAV)
- Remove unused assets before building
- Don't include debug symbols

---

## Step 4: Create the GitHub Release

### Navigate to Releases

1. Go to your repository on GitHub (in your browser)
2. Look at the right sidebar
3. Click **Releases** (or "Create a new release" if it's your first)

If you don't see it:
1. Click the **Code** tab
2. Scroll down and look for "Releases" on the right

### Create a New Release

1. Click **"Draft a new release"** (or "Create a new release")

2. **Choose a tag:**
   - Click "Choose a tag"
   - Type `v1.0.0` (or your version number)
   - Click "Create new tag: v1.0.0 on publish"

3. **Release title:**
   - Enter your game's name
   - Example: "Super Awesome Game - Jam Submission"

4. **Description:**
   Write a description including:
   ```markdown
   ## About
   [One paragraph describing your game]

   ## How to Play
   - **Arrow Keys / WASD** - Move
   - **Space** - Jump
   - **Escape** - Pause

   ## Download
   Download the ZIP file below and extract it. Run `YourGame.exe` to play!

   ## Credits
   - **Programming:** [Names]
   - **Art:** [Names]
   - **Sound:** [Names]
   - **Music:** [Names or source]

   ## Known Issues
   - [Any bugs you know about]

   Made for the Dundee & Angus Game Jam!
   ```

5. **Attach your build:**
   - Scroll down to "Attach binaries"
   - Drag and drop your ZIP file
   - Or click "Attach binaries" and browse for it
   - Wait for the upload to complete

6. **Publish:**
   - Make sure "Set as the latest release" is checked
   - Click **"Publish release"**

---

## Step 5: Verify Your Release

After publishing:

1. **Check the release page** - Does it look right?
2. **Download your own ZIP** - Click the download link
3. **Test the downloaded build** - Extract and run it
4. **Copy the URL** - This is your submission link!

Your release URL looks like:
```
https://github.com/YOUR-USERNAME/YOUR-REPO/releases/tag/v1.0.0
```

---

## Updating Your Release

### Made a mistake? Need to upload a new build?

1. Go to your release page
2. Click **Edit** (pencil icon)
3. You can:
   - Change the description
   - Delete old files (click the X)
   - Upload new files
4. Click **Update release**

### Major Update? Create a New Release

If you're submitting a significantly different version:

1. Create a new release
2. Use a new tag (e.g., `v1.1.0`)
3. Update your submission link if needed

---

## Release Checklist

Before submitting, make sure:

- [ ] Game builds without errors
- [ ] Build tested on your machine
- [ ] Build tested from a different folder (not your project)
- [ ] ZIP file created with all necessary files
- [ ] README/controls included
- [ ] Release created on GitHub
- [ ] Description includes how to play
- [ ] Credits included
- [ ] Download link works
- [ ] Downloaded build runs correctly

---

## After the Jam

### Keep Your Release Available

Don't delete your release after the jam! Judges and players need access.

### Future Updates

After judging, you can:
- Create new releases with bug fixes
- Add builds for other platforms (Mac, Linux, Web)
- Continue developing your game!

### Versioning Tips

Use semantic versioning:
- `v1.0.0` - Initial jam submission
- `v1.0.1` - Bug fixes
- `v1.1.0` - New features added
- `v2.0.0` - Major overhaul

---

## Troubleshooting

### "File too large to upload"

GitHub allows up to 2GB per file. If your ZIP is larger:
- Remove unused assets
- Compress audio files
- Check for duplicate files
- Consider using Git LFS for the repo itself

### "Upload failed"

- Check your internet connection
- Try a smaller file first
- Try a different browser
- Wait a few minutes and try again

### "Release not showing up"

- Make sure you clicked "Publish release"
- Refresh the page
- Check you're on the right repository

### "Download link doesn't work"

- Wait a minute for GitHub to process
- Try downloading in an incognito window
- Check the file actually uploaded (shows file size)

---

## Quick Reference

### Version Tag Format
```
v1.0.0
 │ │ │
 │ │ └── Patch (bug fixes)
 │ └──── Minor (new features)
 └────── Major (big changes)
```

### Release Description Template
```markdown
## [Game Name]

[Brief description]

### How to Play
- [Control] - [Action]
- [Control] - [Action]

### Download & Run
1. Download the ZIP below
2. Extract all files
3. Run [GameName].exe

### Credits
[Your team]

### Made for
Dundee & Angus Game Jam
```

---

## See Also

- [Git Guide](GIT_GUIDE.md) - Git basics
- [For Programmers](FOR_PROGRAMMERS.md) - Build tips
- [GameMaker Guide](GAMEMAKER_GUIDE.md) - GameMaker export details
- [Godot Guide](GODOT_GUIDE.md) - Godot export details
- [Unity Guide](UNITY_GUIDE.md) - Unity build details
