# Guide for Programmers

Tips, tricks, and gotchas for programmers working in a game jam with Git.

---

## Git Gotchas for Game Development

### Binary Files Don't Merge

Unlike code, binary files (images, audio, scenes) **cannot be merged**. If two people edit the same binary file, one person's changes will be lost.

**Solution:** Communicate! Assign ownership of specific files/folders.

### Scene Files Are Dangerous

In Unity, Godot, and GameMaker, scene/room files are the most common source of conflicts because:
- Multiple people often need to edit them
- They contain references to many objects
- They're often in a binary or complex text format

**Solutions:**
1. **One person owns each scene** - Only they edit it
2. **Use prefabs/scenes for reusable parts** - Edit those separately
3. **Communicate before editing scenes** - "I'm editing Level 2!"
4. **Merge often** - Small changes are easier to resolve

### Large Files Slow Down Git

Git isn't great with large files (>50MB). Avoid committing:
- Uncompressed audio (use .ogg or .mp3, not .wav)
- Uncompressed video
- Photoshop/source art files (export to PNG)
- Build outputs (these are in .gitignore anyway)

---

## Testing Before Every Commit

**Never commit broken code.** Before every commit:

1. **Save all files** in your editor and engine
2. **Run the game** and test basic functionality
3. **Check the console** for errors
4. **Build the game** if you've made significant changes

A quick 30-second test can save hours of debugging later.

### The "It Works On My Machine" Problem

Your game might work on your computer but break on your teammate's because of:
- Missing files (forgot to commit something)
- Hardcoded paths (`C:\Users\YourName\...`)
- Different engine versions
- Platform-specific code

**Prevention:**
- Use relative paths, not absolute
- Commit all necessary files
- Agree on engine version with your team
- Pull and test on a fresh clone occasionally

---

## Code Organization Tips

### Keep It Simple

Game jams are about speed. Don't over-engineer:

```
BAD:
AbstractEnemyFactoryInterface -> EnemyFactoryImpl -> EnemyBuilder -> Enemy

GOOD:
Enemy
```

### But Not Too Simple

A little organization goes a long way:

```
Scripts/
  Player/
    PlayerMovement.cs
    PlayerHealth.cs
  Enemies/
    Enemy.cs
    EnemySpawner.cs
  UI/
    MainMenu.cs
    PauseMenu.cs
  Managers/
    GameManager.cs
    AudioManager.cs
```

### Comment the Weird Stuff

You don't need to comment everything, but DO comment:
- Workarounds and hacks
- Magic numbers
- Non-obvious logic

```csharp
// Multiply by 0.7 because the sprite pivot is offset
transform.position.y *= 0.7f;

// HACK: Wait one frame for physics to settle
yield return null;
```

---

## Working with Artists

### Make Swapping Assets Easy

Structure your code so artists can swap placeholder art:
- Use descriptive file names (`player_idle.png`, not `sprite1.png`)
- Keep assets in organized folders
- Don't hardcode asset references if possible

### Document Asset Requirements

Tell artists what you need:
- **Sprite dimensions** (e.g., "Player sprite: 64x64 pixels")
- **Animation frames** (e.g., "Walk cycle: 8 frames")
- **Pivot points** (e.g., "Center pivot" or "Bottom center")
- **File format** (e.g., "PNG with transparency")

### Use Placeholder Colors

When creating placeholder art yourself:
- Use bright, distinct colors (red for enemies, green for pickups)
- Match the dimensions of final art
- Include the name in the image if possible

---

## Merge Conflict Strategies

### For Code Conflicts

1. Read both versions carefully
2. Understand what each change does
3. Keep both changes if they don't interfere
4. Test after resolving

### For Scene/Level Conflicts

Scene conflicts are often impossible to resolve. Instead:

1. **Discard one version** (coordinate with teammate)
2. Have the losing person **redo their changes** manually
3. Or **work from the more complete version**

This is why branches and communication are so important!

### When You're Unsure

Ask! It's better to ask your teammate than to guess wrong and lose work.

---

## Game Jam Speed Tips

### Start with Core Mechanics

Day 1 priority:
1. Player can move
2. Basic game loop works
3. One core mechanic functions

Polish comes later!

### Use Singletons Sparingly (But Use Them)

For game jams, simple singletons are fine:

```csharp
public class GameManager : MonoBehaviour
{
    public static GameManager Instance;

    void Awake()
    {
        Instance = this;
    }
}

// Usage anywhere:
GameManager.Instance.AddScore(100);
```

### Scope Small, Then Add

Better to have a small, polished game than a broken ambitious one.

Start with:
- One level
- One enemy type
- One player ability
- One win condition

Add more only if you have time.

---

## Debugging Tips

### Use Debug Logs Wisely

```csharp
// Good - tells you what's happening
Debug.Log($"Player took {damage} damage, health now {currentHealth}");

// Bad - meaningless
Debug.Log("here");
Debug.Log("1");
Debug.Log("works");
```

### Check the Obvious First

When something breaks:
1. Did you save the file?
2. Did you save the scene?
3. Is the script attached to a GameObject?
4. Are the references assigned in the Inspector?
5. Did you pull the latest changes?

### Git Bisect (Advanced)

If something broke and you don't know when:
1. Find a commit where it worked
2. Find a commit where it's broken
3. Use `git bisect` to find the breaking commit

---

## Quick Reference

### Before You Start Working
```
1. Open GitHub Desktop
2. Fetch origin
3. Pull changes
4. Check with team: "What's everyone working on?"
```

### Before You Commit
```
1. Save all files
2. Test the game runs
3. Check console for errors
4. Review your changes in GitHub Desktop
5. Write a meaningful commit message
```

### When Something Breaks
```
1. Don't panic
2. Check git status - what changed?
3. Test reverting recent changes
4. Ask for help if stuck
```

---

## See Also

- [Git Guide](GIT_GUIDE.md) - Complete Git tutorial
- [Unity Guide](UNITY_GUIDE.md) - Unity-specific tips
- [Godot Guide](GODOT_GUIDE.md) - Godot-specific tips
- [GameMaker Guide](GAMEMAKER_GUIDE.md) - GameMaker-specific tips
