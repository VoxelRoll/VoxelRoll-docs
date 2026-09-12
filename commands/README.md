# Command reference

Every command starts with `/voxelroll`. This page is a lookup reference, not a tutorial.
Most of what these do has a button somewhere in the panel, and the section pages show that
route first.

**Who can run it**

- **player**: anyone connected.
- **GM**: you hold the GM role, or you are a server operator. Most also need a campaign of your
  own running.
- Operator-only commands live under `/voxelroll op` and have [their own section](#server-operator).

**in world** in the Who column means you must be standing inside the campaign's world. That is
the most common reason a token or moment command fails.

**local** means the command runs entirely on your own client against your own files. It
works with no campaign running and never reaches the server.

## Campaigns and sessions

| Command | Who | What it does |
|---|---|---|
| `session join` | player | Joins the session you were invited to. Fails if you are in more than one. |
| `session join <campaign>` | player | Joins by campaign name. |
| `session join <campaign> <gm>` | player | Joins by campaign name and GM, for when two GMs run a campaign with the same name. |
| `session leave` | player | Leaves your current session. |
| `session start` | GM | Starts the session for the campaign you have running. |
| `session stop` | GM | Stops it. Everyone in the session is kicked out of it. |

## Characters and companions

| Command | Who | What it does |
|---|---|---|
| `character <name> assign <campaignName>` | local | Copies one of your local character templates into a campaign you have joined. |
| `companion <name> assign <campaignName>` | local | Same, for a companion template. |
| `companion summon <name>` | player | Summons one of your bonded companions into the world beside you. |
| `companion dismiss` | player | Sends your summoned companion away. |

Assigning makes a per-campaign copy. Editing the copy does not touch the template, so one
template character can join several campaigns.

## Turns and combat

| Command | Who | What it does |
|---|---|---|
| `turn end` | player | Ends your own turn. |
| `turn status` | player | Prints the current turn order and round. |
| `turn ghost` | player | Leaves your body, or returns to it. |
| `turn enter` | GM | Enters turn-based mode. Builds the turn order without starting combat. |
| `turn rollinitiative` | GM | Asks every seated player for an initiative roll. |
| `turn cancelrolls` | GM | Cancels the initiative requests you just sent. |
| `turn rollfor <player>` | GM | Rolls initiative on a player's behalf, for someone away from their keyboard. |
| `turn add <player>` | GM | Adds a player to the turn order after it was built. |
| `turn previous` | GM | Steps the turn order back one entry. |
| `turn startcombat` | GM | Starts combat from the current order. Movement locks to whoever is acting. |
| `turn stopcombat` | GM | Ends combat but keeps the turn order. |
| `turn exitmode` | GM | Leaves turn mode entirely and clears the order. |

## Tokens

The whole `token` tree is GM-only. Everything that repositions something needs you inside
the campaign's world; `remove` and `clear` work from anywhere.

| Command | Who | What it does |
|---|---|---|
| `token move <player> here` | GM, in world | Brings a player to you. |
| `token move <player> <pos>` | GM, in world | Moves a player to a position. |
| `token pull <player>` | GM, in world | Brings a player to you. |
| `token goto <player>` | GM, in world | Teleports you to a player. |
| `token control <player>` | GM, in world | Takes control of a player's body. |
| `token release` | GM | Gives back whatever you are controlling. |
| `token remove <player>` | GM | Removes a player's token. |
| `token party summon <player>` | GM, in world | Summons a player's party to them. |
| `token party dismiss <player>` | GM | Sends that party away. |

NPC and monster tokens:

| Command | Who | What it does |
|---|---|---|
| `token npc move <token> here\|<pos>` | GM, in world | Moves a spawned token to you or to a position. |
| `token npc pull <token>` | GM, in world | Brings a token to you. |
| `token npc goto <token>` | GM, in world | Teleports you to a token. |
| `token npc control <token>` | GM, in world | Takes control of a token and plays it directly. |
| `token npc remove <token>` | GM | Removes one spawned token. |
| `token npc save-to-template <token>` | GM | Saves this token's current state back to its template. |
| `token npc reveal here` | GM, in world | Reveals hidden tokens around you. |
| `token npc clear` | GM | Clears stray tokens left by your own stopped campaigns. |
| `token npc clear loose` | GM | Clears tokens that lost their owning campaign. |
| `token npc clear all` | GM | Clears strays from every campaign. Operator territory, use with care. |

## Scenes and moments

Moments are GM-authored scenes inside a world. `<path>` is the moment's path in the
folder tree, the way `moment list` prints it.

| Command | Who | What it does |
|---|---|---|
| `moment list [folder]` | GM | Lists moments, optionally inside one folder. |
| `moment create <name> [folder]` | GM | Creates a moment, optionally inside a folder. |
| `moment rename <path> <newName>` | GM | Renames a moment. |
| `moment move <path> <destination>` | GM | Moves a moment to another folder. |
| `moment delete <path>` | GM | Deletes a moment. |
| `moment folder create <path>` | GM | Creates a folder. |
| `moment folder rename <path> <newName>` | GM | Renames a folder. |
| `moment folder delete <path>` | GM | Deletes a folder. |
| `moment bounds <path> <x1> <y1> <z1> <x2> <y2> <z2>` | GM | Sets the moment's zone from two corners. |
| `moment spawn <path>` | GM | Sets where players arrive in the moment. |
| `moment activate <path>` | GM | Makes the moment live. |
| `moment deactivate <path>` | GM | Turns it off. |
| `moment go <path>` | GM | Sends yourself into the moment. |
| `moment send <players> <path>` | GM | Sends the named players into it. |
| `moment regroup <path>` | GM | Pulls players back out of it. |
| `moment spotlight <path>` | GM | Cuts the table's view to that moment so everyone can watch. |

## Worlds

| Command | Who | What it does |
|---|---|---|
| `world enter` | player | Enters the campaign's world. |
| `world leave` | player | Returns you to where you came from. |
| `world park` | player | Parks the world you are in. |
| `world sync` | player | Forces a sync of the world's saved state. |

## World versions and backups

All of these are **local**: they run on your own client against your own copies of a
campaign's worlds, and work with no campaign running. `<n>` is a version number from
`world versions list`.

| Command | What it does |
|---|---|
| `world list <campaignName>` | Lists the worlds a campaign owns. |
| `world add <campaignName> <name> [seed]` | Adds a world to a campaign, optionally from a seed. |
| `world rename <campaignName> <world> <newName>` | Renames a world. |
| `world switch <campaignName> <world>` | Makes a different world the campaign's active one. |
| `world presence` | Shows which of your worlds exist on the server you are on. |
| `world delete-local <campaignName>` | Deletes your local copy. |
| `world remove-server <campaignName>` | Removes the server's copy. |
| `world versions list` | Lists stored versions of the current world. |
| `world versions diff <n>` | Shows what changed in that version. |
| `world versions pin <name>` | Pins the current version under a name so it is never collected. |
| `world versions pin-version <n> <name>` | Pins an older version by number. |
| `world versions unpin <id>` | Removes a pin. |
| `world versions rename-pin <id> <name>` | Renames a pin. |
| `world versions rollback <target>` | Rolls the world back to a version or pin. |
| `world versions delete <n>` | Deletes one version. |
| `world versions gc` | Collects unpinned versions to reclaim disk. |
| `world versions lines` | Lists the server lines your copies came from. |
| `world versions rename-line <serverId> <name>` | Names a server line so you can tell them apart. |
| `world versions delete-line <serverId>` | Forgets a server line. |
| `world snapshot take <name>` | Takes a named snapshot. |
| `world snapshot list` | Lists snapshots. |
| `world snapshot delete <name>` | Deletes one. |
| `world restore <campaignName> <target>` | Restores a world from a version, pin, or snapshot. |
| `world restore-cancel <campaignName> <world>` | Cancels a restore in progress. |
| `world export <campaignName> <target> <name>` | Exports a world to a `.vrw` file. |
| `world import <campaignName> <file>` | Imports a `.vrw` file into a campaign. |
| `world import-folder <campaignName> <world> <path> <centreX> <centreZ> <radius>` | Imports a Minecraft save folder. |
| `world import-azgaar <campaignName> <world> <path> ...` | Imports an Azgaar map as terrain. |
| `world import-heightmap <campaignName> <world> <path> ...` | Imports a heightmap image as terrain. |

## Environment

Time and weather inside the campaign's world. GM only.

| Command | Who | What it does |
|---|---|---|
| `world time` | GM | Reports the world's current time. |
| `world time day\|noon\|night\|midnight` | GM | Jumps to that time. |
| `world time set <ticks>` | GM | Sets an exact time in ticks. |
| `world time freeze` | GM | Stops the clock. |
| `world time resume` | GM | Starts it again. |
| `world weather clear\|rain\|thunder` | GM | Sets the weather. |

## Schematics

| Command | Who | What it does |
|---|---|---|
| `paste <name>` | GM | Pastes an uploaded schematic at your position. |
| `paste <name> <pos>` | GM | Pastes it at a position. |
| `paste undo` | GM | Undoes your last paste. |

## Server operator

Everything under `/voxelroll op` needs operator permission, regardless of role. These take
player names rather than requiring the target online, so you can clean up after someone who
has logged off.

**Roles and campaigns**

| Command | What it does |
|---|---|
| `op addgm <player>` | Grants the GM role. Survives restarts. |
| `op removegm <player>` | Revokes it, and stops any campaign that player has running. |
| `op campaigns` | Lists running campaigns. |
| `op campaigns records` | Lists stored campaign ownership records, live or orphaned. |
| `op campaigns purge <campaignId>` | Deletes an orphaned record. |
| `op stopcampaign <player>` | Force-stops a GM's running campaign. |

**Turns**

| Command | What it does |
|---|---|
| `op turn status <player>` | Inspects another GM's turn state. |
| `op turn advance <player>` | Forces their turn order forward. |
| `op turn stopcombat <player>` | Forces combat to end. |
| `op turn exitmode <player>` | Forces turn mode off. |
| `op turn unghost <player>` | Puts a player back in their body. |

**Worlds**

| Command | What it does |
|---|---|
| `op worlds` | Lists claimed dimension pool slots. |
| `op worlds release <campaignId>` | Frees a campaign's slot. |
| `op worlds park <campaignId>` | Parks a campaign's world. |
| `op worlds regenerate <campaignId>` | Regenerates it. |
| `op worlds delta <campaignId>` | Reports what has changed since the last sync. |
| `op worlds restores` | Lists restores in progress. |
| `op worlds restores cancel <campaignId>` | Cancels one. |
| `op worlds archive` | Lists archived worlds. |
| `op worlds archive purge <campaignId>` | Deletes an archived world permanently. |

[Back to the manual index](../)
