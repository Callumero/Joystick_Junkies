# Guide for Artists

Tips for artists working in a game jam, especially when using Git with a team.

---

## The Placeholder Strategy

**This is the most important concept for artists in a game jam!**

### Why Placeholders First?

In a game jam, programmers need something to work with immediately. If they wait for final art, they can't test their code. The solution:

1. **Create simple placeholder art first** (colored boxes/shapes)
2. **Give it to programmers right away**
3. **Replace with real art later**

### What Makes a Good Placeholder?

Good placeholders have:
- **Correct dimensions** (same size as final art)
- **Clear colors** (different color for each thing)
- **Readable labels** (optional: write what it is)

Example placeholders:
- **Player:** Blue 64x64 square
- **Enemy:** Red 64x64 square
- **Coin/Pickup:** Yellow 32x32 circle
- **Platform:** Green 128x32 rectangle

### Placeholder Naming Convention

Use clear names that match the final art:
```
player_idle_placeholder.png  -> player_idle.png
enemy_walk_placeholder.png   -> enemy_walk.png
```

Or use folders:
```
Sprites/
  Placeholder/
    player.png
  Final/
    player.png
```

### How to Replace Placeholders

When your real art is ready:
1. Make sure it's the **exact same dimensions**
2. Use the **exact same filename**
3. Replace the placeholder file
4. Test the game to make sure it still works!

If dimensions need to change, **communicate with your programmer(s) first!**

---

## Asset Dimensions

### Common Sizes

| Asset Type | Typical Size | Notes |
|------------|--------------|-------|
| Player sprite | 32x32, 64x64 | Match your game's scale |
| Enemies | 32x32, 64x64 | Often same as player |
| Tiles | 16x16, 32x32 | Must tile seamlessly |
| UI buttons | 128x64, 200x50 | Varies by design |
| Icons | 32x32, 64x64 | Keep consistent |
| Background | 1920x1080 | Or your game resolution |

### Ask Your Programmer!

Before starting art, ask:
- What resolution is the game?
- What size should sprites be?
- What's the art style/pixel size?
- How many animation frames are needed?

---

## Animation Frames

### Frame Counts

Common animation frame counts:
- **Idle:** 2-4 frames
- **Walk:** 4-8 frames
- **Run:** 6-8 frames
- **Jump:** 2-3 frames (up, peak, fall)
- **Attack:** 3-6 frames

### Sprite Sheet vs Individual Files

**Sprite Sheet:** All frames in one image
```
player_walk_sheet.png (contains 8 frames in a row)
```

**Individual Files:** Each frame separate
```
player_walk_1.png
player_walk_2.png
player_walk_3.png
...
```

Ask your programmer which they prefer! Most engines handle both.

### Animation Timing

Let programmers know the intended frame rate:
- "Walk animation: 12 FPS"
- "Attack animation: faster, 24 FPS"

---

## File Formats

### For 2D Sprites: PNG

Always use PNG for sprites because:
- Supports transparency
- Lossless quality
- Small file size for game art

**Export settings:**
- PNG-8 for simple art (smaller files)
- PNG-24/32 for detailed art with transparency

### For Backgrounds: PNG or JPG

- **PNG:** If it needs transparency
- **JPG:** If no transparency needed (smaller file size)

### For Audio: OGG or MP3

If you're also doing sound:
- **OGG:** Best for games (small, good quality)
- **MP3:** Also fine, slightly larger
- **Avoid WAV:** Too large for version control

---

## Folder Organization

Keep assets organized so programmers can find them:

```
Assets/
  Sprites/
    Player/
      player_idle.png
      player_walk.png
      player_jump.png
    Enemies/
      slime_idle.png
      slime_walk.png
    Environment/
      grass_tile.png
      platform.png
    UI/
      button_play.png
      button_quit.png
  Audio/
    Music/
      main_theme.ogg
    SFX/
      jump.ogg
      coin_pickup.ogg
```

---

## Using Git as an Artist

### When to Commit

Commit your work when you have:
- A complete placeholder for something new
- A finished or improved asset
- A set of related assets (e.g., all walk animation frames)

### Good Commit Messages

```
Good:
"Add player walk animation (8 frames)"
"Replace placeholder coin with final art"
"Add grass tileset"

Bad:
"art"
"stuff"
"new images"
```

### Communicate About Assets

When you finish an asset:
1. Commit and push it
2. Tell your team (Discord/chat)
3. Let programmers know they can use it

Example message:
> "Just pushed the player walk animation - 8 frames at 64x64, check Sprites/Player/"

---

## Collaborating with Programmers

### Tell Programmers What You Need to Know

Before starting:
- "What size should the player sprite be?"
- "How many frames for the walk animation?"
- "What format do you want the sprite sheets?"

### Tell Programmers What You're Making

Keep them updated:
- "Working on enemy sprites today"
- "Player art will be ready in 2 hours"
- "I'm updating the UI - don't use the old buttons"

### Pivot Points and Origins

Some things programmers care about:
- **Pivot point:** Where the "center" of a sprite is
- **Consistent sizing:** All frames same dimensions
- **Padding:** Sometimes sprites need empty space around them

Ask if you're not sure!

---

## Quick Art Tips for Game Jams

### Keep It Simple

- Simpler art is faster to make
- Consistent simple art > inconsistent complex art
- Pixel art at low resolution is very jam-friendly

### Use a Limited Palette

- Pick 8-16 colors and stick to them
- Makes art cohesive
- Faster decisions

### Silhouettes First

- If the silhouette reads well, the art works
- Test by squinting or making it tiny
- Player and enemies should look different at a glance

### Iterate, Don't Perfect

1. Block out shapes (5 minutes)
2. Add basic color (5 minutes)
3. Add detail if time permits
4. Polish only at the end

---

## Tools

### Free Art Tools

- **Aseprite** (paid, but cheap) - Best for pixel art
- **Piskel** (free, web-based) - Good for pixel art
- **GIMP** (free) - Photoshop alternative
- **Krita** (free) - Great for painting
- **Inkscape** (free) - Vector art

### Free Sound Tools

- **Audacity** (free) - Record and edit audio, essential for any sound work
- **BFXR** (free, web-based) - Generate retro game sound effects instantly
- **SFXR** (free) - The original 8-bit sound effect generator
- **ChipTone** (free, web-based) - More advanced retro sound generator
- **Bosca Ceoil** (free) - Simple music creation, great for chiptunes
- **LMMS** (free) - Full music production (like a free FL Studio)
- **BeepBox** (free, web-based) - Easy chiptune music in your browser
- **Freesound.org** (free library) - Huge library of free sound effects (check licenses!)

### Quick Sound Tips

- **Start with placeholder sounds too!** - Use BFXR to generate quick "bleep" and "boop" sounds
- **Keep sounds short** - Most game SFX are under 1 second
- **Export as OGG** - Smaller files than MP3, great quality
- **Test volume levels** - Sounds should be balanced with each other

### Quick Asset Resources

If you need assets fast (check licenses!):
- [OpenGameArt.org](https://opengameart.org) - Art and audio
- [itch.io Game Assets](https://itch.io/game-assets) - Tons of free packs
- [Kenney.nl](https://kenney.nl) - Public domain art and audio!
- [Freesound.org](https://freesound.org) - Sound effects library

Always credit assets you didn't make!

---

## See Also

- [Git Guide](GIT_GUIDE.md) - Complete Git tutorial
- [Unity Guide](UNITY_GUIDE.md) - Unity-specific tips
- [Godot Guide](GODOT_GUIDE.md) - Godot-specific tips
- [GameMaker Guide](GAMEMAKER_GUIDE.md) - GameMaker-specific tips
