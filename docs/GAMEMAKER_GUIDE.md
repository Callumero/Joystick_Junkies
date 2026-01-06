# GameMaker + Git Guide

GameMaker-specific tips for working with Git in a game jam.

---

## Why We Recommend GameMaker

GameMaker is excellent for game jams because:

1. **Fast to prototype** - Drag-and-drop or GML, both work quickly
2. **Built-in room editor** - Level design is intuitive
3. **Great 2D support** - Perfect for jam-scale games
4. **Easy exports** - One-click Windows builds
5. **Beginner-friendly** - Low barrier to entry

---

## Project Structure

```
GameMaker/
  Dundee & Angus Game Jam.yyp    <- Main project file
  Dundee & Angus Game Jam.resource_order

  fonts/              <- Font resources
  objects/            <- Game objects
  options/            <- Platform export settings
  rooms/              <- Levels/scenes
  scripts/            <- GML scripts
  sounds/             <- Audio files
  sprites/            <- Sprite images
  tilesets/           <- Tile assets
  datafiles/          <- Included files
```

---

## What to Commit

**DO commit:**
- `*.yyp` - Project file
- `*.yy` - Resource definition files
- `*.gml` - Scripts
- `*.png` - Sprites (in the sprites folder)
- All resource folders

**DON'T commit (already in .gitignore):**
- `cache/` folders - Build cache
- `*.zip`, `*.yyz` - Exported projects
- `output/` folders - Build outputs

---

## GameMaker-Specific Git Gotchas

### 1. Room Files Cause Conflicts

GameMaker room files (`.yy` in the `rooms/` folder) contain:
- All instances in the room
- Instance positions
- Layer settings
- Room properties

Two people editing the same room = guaranteed conflicts!

**Solutions:**
- **Assign room ownership:** "Jamie owns rm_level1"
- **Use object spawning:** Spawn instances via code instead of placing in room
- **Communicate:** "I'm editing the main room!"

### 2. Resource Order Matters

The `.resource_order` file tracks the order of resources in the IDE. It changes often but usually doesn't cause issues if it conflicts.

**If it conflicts:** Accept either version, GameMaker will sort it out.

### 3. Object Files Can Conflict

Object `.yy` files contain event code and variable definitions. Conflicts here are manageable because GML code is text.

**Tip:** Keep objects focused on one purpose to reduce conflicts.

### 4. Sprite Folders Contain Multiple Files

Each sprite has:
- A `.yy` definition file
- PNG files for each frame
- Layer information

Commit them all together when you add/modify sprites.

---

## Opening the Project

### First Time Setup

1. Open **GameMaker**
2. Click **Open**
3. Navigate to the `GameMaker` folder in this template
4. Select `Dundee & Angus Game Jam.yyp`
5. Click **Open**

### After Pulling Changes

After pulling changes from Git:
1. Open GameMaker
2. If the project is already open, close and reopen it
3. GameMaker will reload all resources

If things look wrong:
1. Close GameMaker completely
2. Pull again in GitHub Desktop
3. Reopen the project

---

## GameMaker + Git Workflow

### Before Starting Work

1. **Open GitHub Desktop** and pull latest changes
2. **Close GameMaker** if it's open
3. **Reopen the project** in GameMaker
4. Tell your team what you're working on

### While Working

1. **Save often** (Ctrl+S)
2. **Test often** (F5)
3. **Commit small changes frequently**

### Committing Changes

GameMaker changes often involve multiple files. For example, adding a sprite:
```
sprites/spr_player/spr_player.yy
sprites/spr_player/layers/.../[various layer files]
sprites/spr_player/[frame].png
```

Commit all related files together!

---

## Building Your Game

### Creating a Build

1. Go to **Build > Create Executable**
2. Choose your platform (Windows recommended)
3. Select a location **outside** your project folder
4. Click **Save**
5. Wait for the build to complete

### Export Options

For the jam, we recommend:
- **Windows (YYC)** - Best performance, needs Visual Studio
- **Windows (VM)** - Faster to build, slightly slower game
- **HTML5** - Runs in browser, easy to share

### Build Folder Structure

Keep builds separate from your project:
```
MyGameJam/
  GameMaker/       <- Your GameMaker project
  Builds/          <- Build outputs (gitignored)
    Windows/
      MyGame.exe
```

### Testing Before Submission

1. Build your game
2. **Copy the entire build folder** to another location
3. Run it from there
4. This tests it works without GameMaker

---

## Common GameMaker Issues

### "Resource Not Found" Errors

If GameMaker can't find a resource:
- It was renamed or deleted
- The files didn't sync properly

**Fix:** Check your Git history, or recreate the resource.

### Objects Not Appearing in Room

If placed instances don't show up:
- Check they're on a visible layer
- Check the object has a sprite
- Check the draw event isn't empty/broken

### Code Not Running

If code doesn't seem to work:
- Check the event type (Step vs Create vs Draw)
- Check variable scope (instance vs global)
- Use `show_debug_message()` to debug

### After Pull, Everything is Broken

Try in order:
1. Close GameMaker completely
2. Pull again in GitHub Desktop
3. Reopen the project
4. If still broken, check with your teammate about their changes

---

## GML Quick Reference

### Movement (Simple)

```gml
// In Step event
if (keyboard_check(vk_right)) {
    x += 4;
}
if (keyboard_check(vk_left)) {
    x -= 4;
}
```

### Movement (Smooth)

```gml
// In Create event
spd = 4;

// In Step event
var _h = keyboard_check(vk_right) - keyboard_check(vk_left);
var _v = keyboard_check(vk_down) - keyboard_check(vk_up);
x += _h * spd;
y += _v * spd;
```

### Collision

```gml
// Check collision before moving
if (!place_meeting(x + _h * spd, y, obj_wall)) {
    x += _h * spd;
}
if (!place_meeting(x, y + _v * spd, obj_wall)) {
    y += _v * spd;
}
```

### Creating Instances

```gml
instance_create_layer(x, y, "Instances", obj_bullet);
```

### Room Navigation

```gml
room_goto(rm_level2);
room_restart();
```

### Global Variables

```gml
// Set (anywhere)
global.score = 0;

// Access (anywhere)
global.score += 10;
```

---

## Recommended Project Organization

### Objects

```
obj_player
obj_enemy_basic
obj_enemy_boss
obj_bullet_player
obj_bullet_enemy
obj_pickup_health
obj_pickup_coin
obj_wall
obj_game_controller   <- Persistent, manages game state
```

### Scripts

```
scr_movement          <- Shared movement functions
scr_damage            <- Health/damage functions
scr_save_load         <- Save game functions
```

### Rooms

```
rm_menu
rm_level_1
rm_level_2
rm_game_over
```

---

## Useful GameMaker Features

### Persistent Objects

For objects that survive room changes:
1. Open the object
2. Check **Persistent** in the options

Good for: Game managers, music controllers, player (sometimes)

### Parent Objects

For shared behavior:
1. Create a parent object (e.g., `obj_enemy_parent`)
2. Add shared events to the parent
3. In child objects, set Parent to `obj_enemy_parent`

### Instance Variables

Define defaults in Create event:
```gml
hp = 100;
speed = 4;
can_jump = true;
```

### Alarms

For delayed actions:
```gml
// In Create or whenever
alarm[0] = room_speed * 2; // 2 seconds

// In Alarm 0 event
instance_destroy();
```

---

## Quick Reference

### Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Save | Ctrl+S |
| Run | F5 |
| Stop | F6 |
| Clean | Ctrl+Shift+C |
| Find | Ctrl+F |
| Find in All Scripts | Ctrl+Shift+F |

### Common Functions

| Function | Purpose |
|----------|---------|
| `keyboard_check(key)` | Is key held? |
| `keyboard_check_pressed(key)` | Was key just pressed? |
| `place_meeting(x, y, obj)` | Collision check |
| `instance_create_layer()` | Spawn object |
| `instance_destroy()` | Remove object |
| `room_goto(room)` | Change room |
| `draw_sprite(spr, img, x, y)` | Draw sprite |
| `draw_text(x, y, string)` | Draw text |

---

## See Also

- [Git Guide](GIT_GUIDE.md) - Complete Git tutorial
- [For Programmers](FOR_PROGRAMMERS.md) - General programming tips
- [For Artists](FOR_ARTISTS.md) - Art and asset tips
