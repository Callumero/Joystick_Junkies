# Dundee & Angus Game Jam Template

Starter templates for **Unity**, **Godot**, and **GameMaker**, complete with smart `.gitignore` files and comprehensive guides to help you focus on making games, not setting things up.

---

## Quick Start

### 1. Fork This Repository

1. Click the **"Fork"** button at the top of this page
2. Select your account
3. You now have your own copy!

### 2. Add Your Team

1. Go to your fork's **Settings > Collaborators**
2. Click **Add people**
3. Add your teammates by username or email

### 3. Clone and Start Making

1. Open **GitHub Desktop**
2. Clone your fork to your computer
3. Open the `Unity/`, `Godot/`, or `GameMaker/` folder in your engine
4. Start making your game!

**New to Git?** Read the [complete Git guide](docs/GIT_GUIDE.md) for step-by-step instructions.

---

## Game Jam Rules

Read the full [Game Jam Rules](docs/GAME_JAM_RULES.md) for:
- Jam schedule and deadlines
- Team size limits
- Submission requirements
- What you can and cannot use

---

## Why We Recommend GameMaker

For the Dundee & Angus Game Jam, we recommend **GameMaker** because:

1. **Fastest prototyping** - Get a playable game running in minutes
2. **Beginner-friendly** - Drag-and-drop or simple code, your choice
3. **Built-in tools** - Room editor, sprite editor, everything in one place
4. **Easy exports** - One-click Windows builds
5. **Great for 2D** - Perfect for jam-sized games
6. **Free tier available** - Export to Windows for free

That said, use whatever engine you're most comfortable with! A game you can finish beats a game you can't.

---

## Choose Your Engine

This template includes starter projects for three engines:

| Engine | Folder | Best For |
|--------|--------|----------|
| **GameMaker** | `GameMaker/` | Fast 2D games, beginners |
| **Godot 4** | `Godot/` | 2D/3D games, open source |
| **Unity** | `Unity/` | 2D/3D games, C# developers |

### Engine-Specific Guides

Each guide covers Git workflows, common issues, and tips specific to that engine:

- [GameMaker + Git Guide](docs/GAMEMAKER_GUIDE.md)
- [Godot + Git Guide](docs/GODOT_GUIDE.md)
- [Unity + Git Guide](docs/UNITY_GUIDE.md)

---

## Guides by Role

### For Programmers
- Git gotchas specific to game development
- Merge conflict strategies
- Code organization tips
- Testing before commits

[Read the Programmer Guide](docs/FOR_PROGRAMMERS.md)

### For Artists
- The placeholder art strategy (create boxes first!)
- Asset dimensions and formats
- How to use Git for art files
- Replacing placeholders

[Read the Artist Guide](docs/FOR_ARTISTS.md)

---

## Using Git

Never used Git before? No problem! We have a complete beginner's guide:

[Git Guide for Complete Beginners](docs/GIT_GUIDE.md)

The guide covers:
- Installing GitHub Desktop (Windows)
- Forking and cloning
- Daily workflow (pull, commit, push)
- **Using branches** (highly recommended!)
- Working with your team
- Fixing common problems

### The Golden Rules

1. **Always pull before you start working**
2. **Commit often with descriptive messages**
3. **Use branches for features**
4. **Communicate with your team**

---

## Submitting Your Game (GitHub Releases)

When the jam ends, submit your game using GitHub Releases.

**[Read the full Releasing Guide](docs/RELEASING_YOUR_GAME.md)** for detailed step-by-step instructions.

### Quick Summary

1. **Build your game** from your engine (Windows recommended)
2. **Test the build** - run it outside your project folder
3. **Create a ZIP** with all necessary files
4. **Create a GitHub Release:**
   - Go to your repo > Releases > "Create a new release"
   - Tag it `v1.0.0`
   - Add a description with controls and credits
   - Attach your ZIP file
   - Publish!
5. **Share the release URL** - that's your submission link!

### Tips for a Good Release

- **Test your build** before uploading - run it from a different folder
- **Include a README** in your ZIP - controls, credits, known issues
- **Download and test** your own release to make sure it works

---

## Project Structure

```
Dundee-Angus-Game-Jam-Template/
  README.md               <- You are here
  LICENSE                 <- Project license
  .gitignore              <- Files to ignore

  GameMaker/              <- GameMaker project (recommended)
  Godot/                  <- Godot 4.x project
  Unity/                  <- Unity project

  docs/                     <- Guides and documentation
    GIT_GUIDE.md            <- Git tutorial
    GAME_JAM_RULES.md       <- Jam rules
    FOR_PROGRAMMERS.md      <- Programmer tips
    FOR_ARTISTS.md          <- Artist tips
    GAMEMAKER_GUIDE.md      <- GameMaker + Git
    GODOT_GUIDE.md          <- Godot + Git
    UNITY_GUIDE.md          <- Unity + Git
    RELEASING_YOUR_GAME.md  <- How to submit your game
```

---

## Getting Help

- Read the guides in the `docs/` folder
- Ask your teammates
- Ask the jam organizers
- Check the [GitHub Desktop documentation](https://docs.github.com/en/desktop)

---

## License

This template is released under the [Unlicense](LICENSE) - do whatever you want with it!

Your game and its assets belong to you and your team.

---

Good luck with the jam!
