# VoxelRoll manual

VoxelRoll is a mod for running tabletop RPG sessions inside Minecraft. One player
runs the game as GM. Everyone else plays a character. Pressing your inventory key
opens that character's sheet instead: abilities, skills and attacks, spells, and
background.

The server does the bookkeeping a table normally does on paper. It tracks whose turn
it is and holds everyone else in place until their turn comes around. It rolls every
die itself and writes the result to a shared log, so nobody has to trust a
client-side dice mod, and the GM's hidden rolls stay hidden. The GM can move the
party into a world built for the campaign, fill it with tokens for NPCs and monsters,
and follow each group separately when the party splits up.

This manual is written section by section. Anything not linked below is not written
yet.

## Keybinds

| Key | Action                                                                          |
| --- | ------------------------------------------------------------------------------- |
| `C` | Open the VoxelRoll panel                                                        |
| `G` | Hold for the quick roll wheel                                                   |
| `H` | Toggle ghost mode (leave or return to your body)                                |
| `B` | Toggle the session HUD                                                          |
| `V` | Confirm what you are placing: a crosshair-targeted token move, or a moment area |

All are rebindable in Minecraft's Controls menu, under Game.

## Sections

**Playing**

- [Getting started](getting-started/): requirements, installation, your first session
- [Campaigns and sessions](campaigns/): creating a campaign, invites, rosters, joining a session
- [Characters](characters/): sheet sections, building a character, bringing one into a game
- **Companions**: building, bonding to a character, playing one
- **Dice and rolling**: roll modes, GM-only rolls, roll requests, roll history
- **Turns and combat**: initiative, the movement lock, ghost mode

**Running a game**

- **GM tools**: the encounter screen, NPC and monster templates, tokens, taking
  control
- **Scenes**: moments, spotlight, running a split party
- **Worlds**: campaign worlds, entering and leaving, schematics, environment,
  versions

**Server admin**

- **Server setup**: installing on a dedicated server, granting the GM role, operator
  commands, where data is stored

**Reference**

- [Command reference](commands/): every `/voxelroll` command in one place

## Feedback and bugs

If you have feedback or find a bug, please report it here:
[issue tracker](https://github.com/VoxelRoll/VoxelRoll-docs/issues).
