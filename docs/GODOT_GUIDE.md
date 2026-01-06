# Godot + Git Guide

Godot-specific tips for working with Git in a game jam.

---

## Project Structure

```
Godot/
  project.godot     <- Main project file
  icon.svg          <- Project icon
  scenes/           <- Your scene files (.tscn)
  scripts/          <- Your GDScript files (.gd)
  assets/           <- Sprites, audio, etc.
  .godot/           <- GENERATED (gitignored)
```

---

## What to Commit

**DO commit:**
- `project.godot` - Project configuration
- `*.tscn` - Scene files
- `*.gd` - Scripts
- `*.tres` - Resources
- All your assets (sprites, audio, etc.)
- `export_presets.cfg` - If you want shared export settings

**DON'T commit (already in .gitignore):**
- `.godot/` - Editor cache, regenerated on open
- `*.import` - Import cache files

---

## Godot-Specific Git Gotchas

### 1. Scene Files (.tscn) Cause Conflicts

Godot scene files are text-based (good!) but they contain:
- Node hierarchy
- All property values
- Resource references

Two people editing the same scene = conflicts.

**Solutions:**
- **Assign scene ownership:** "Alex owns main_menu.tscn"
- **Use inherited scenes:** Create base scenes and inherit from them
- **Use composition:** Small scenes combined in code
- **Communicate:** "I'm editing level_1.tscn!"

### 2. Resource Files (.tres) Can Conflict

`.tres` files store reusable resources. Same rules as scenes - coordinate edits!

### 3. The .godot Folder is Local Only

The `.godot/` folder contains:
- Imported asset cache
- Editor layout
- Editor state

This is regenerated when anyone opens the project. **Never commit it.**

### 4. GDScript is Text-Friendly

Good news! GDScript files (`.gd`) are plain text and merge well. Code conflicts are usually easy to resolve.

---

## Opening the Project

### First Time Setup

1. Open **Godot 4.x** (make sure it's version 4!)
2. Click **Import**
3. Navigate to the `Godot` folder in this template
4. Select `project.godot`
5. Click **Import & Edit**

First open will take a moment as Godot imports assets.

### After Pulling Changes

After pulling changes from Git:
1. Open Godot
2. It may reimport some assets (watch the bottom progress bar)
3. Wait for imports to complete before working

If things look wrong:
1. Try **Project > Reload Current Project**
2. Or close and reopen Godot

---

## Godot + Git Workflow

### Before Starting Work

1. **Open GitHub Desktop** and pull latest changes
2. **Open Godot** and wait for any reimports
3. Tell your team what you're working on

### While Working

1. **Save scenes often** (Ctrl+S)
2. **Commit small changes frequently**
3. **Test your game runs** (F5) before committing

### Committing Changes

In GitHub Desktop, you'll see files like:
```
scenes/player.tscn
scripts/player.gd
assets/sprites/player.png
project.godot
```

Commit related files together (e.g., a scene and its script).

---

## Building Your Game

### Setting Up Export

1. Go to **Project > Export**
2. Click **Add...**
3. Select your platform (Windows Desktop recommended)
4. Download the export template if prompted
5. Configure export options

### Creating a Build

1. Go to **Project > Export**
2. Select your export preset
3. Click **Export Project**
4. Choose a folder **outside** your Godot project
5. Wait for export to complete

### Build Folder Structure

Keep builds separate from your project:
```
MyGameJam/
  Godot/            <- Your Godot project
  Builds/           <- Build outputs (gitignored)
    Windows/
      MyGame.exe
```

### Testing Before Submission

1. Export your game
2. **Copy the entire export folder** to another location
3. Run it from there
4. This tests it works without Godot

---

## Common Godot Issues

### "Invalid Resource" Errors

If you see errors about invalid resources:
- A file was moved or renamed
- A reference path is broken

**Fix:** Check the scene in the Inspector, update the path.

### "Missing Node" Warnings

If nodes show as missing:
- The scene file got out of sync
- A custom class was renamed/deleted

**Fix:** Remove and re-add the node, or check your scripts.

### Scene Won't Open After Pull

Try in order:
1. **Reload the project** (Project > Reload Current Project)
2. Close and reopen Godot
3. Delete `.godot/` folder and reopen (forces reimport)
4. Ask your teammate what they changed

### Scripts Not Running

If scripts don't seem to work:
- Check they're attached to the right node
- Check the script path in the Inspector
- Look for errors in the Output panel (bottom)

---

## Recommended Project Structure

```
Godot/
  project.godot

  scenes/
    player/
      player.tscn
    enemies/
      enemy.tscn
    levels/
      level_1.tscn
    ui/
      main_menu.tscn
      pause_menu.tscn

  scripts/
    player/
      player.gd
    enemies/
      enemy.gd
    managers/
      game_manager.gd
    ui/
      main_menu.gd

  assets/
    sprites/
      player/
      enemies/
      environment/
    audio/
      music/
      sfx/
    fonts/
```

---

## Useful Godot Features

### Autoload (Singletons)

For managers that exist throughout your game:

1. **Project > Project Settings > Autoload**
2. Add your script (e.g., `game_manager.gd`)
3. Access anywhere: `GameManager.score += 10`

### Groups

Tag nodes for easy finding:
```gdscript
# In enemy script
func _ready():
    add_to_group("enemies")

# Elsewhere
var enemies = get_tree().get_nodes_in_group("enemies")
```

### Signals

For clean communication between nodes:
```gdscript
# In player.gd
signal health_changed(new_health)

func take_damage(amount):
    health -= amount
    health_changed.emit(health)

# In health_bar.gd
func _ready():
    player.health_changed.connect(_on_health_changed)

func _on_health_changed(new_health):
    value = new_health
```

---

## Quick Reference

### Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Save Scene | Ctrl+S |
| Save All | Ctrl+Shift+S |
| Run Game | F5 |
| Run Current Scene | F6 |
| Stop Running | F8 |
| Quick Open | Ctrl+Shift+O |

### Common GDScript

```gdscript
# Node reference
@onready var sprite = $Sprite2D

# Export variable (shows in Inspector)
@export var speed: float = 200.0

# Signal
signal died

# Movement
func _physics_process(delta):
    var direction = Input.get_vector("left", "right", "up", "down")
    velocity = direction * speed
    move_and_slide()
```

---

## See Also

- [Git Guide](GIT_GUIDE.md) - Complete Git tutorial
- [For Programmers](FOR_PROGRAMMERS.md) - General programming tips
- [For Artists](FOR_ARTISTS.md) - Art and asset tips
