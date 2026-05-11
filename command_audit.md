# instellar cheating
instellar cheat sheet
---

## Private messages

`/whisper`, `/msg`, `/tell` — Send a message to one player without everyone else seeing it. Same pattern everywhere: command, player name, then the message.

`/interactivechat` with `viewitem`, `viewinv`, or `viewender` — Plugin ([InteractiveChat](https://hangar.papermc.io/LOOHP/InteractiveChat)) that lets people share an item, inventory snapshot, or ender chest in chat. Viewers open a read-only menu; the long hex string is an id for that snapshot.

`/venturechat …` — **VentureChat**: extra chat channels (staff chat, local chat, etc.). Subcommands come from `/venturechat help` on that server.

---

## Teams (built into Minecraft)

`/team …`, `/teammsg …` — Uses scoreboard teams: who’s on which team, prefixes, friendly fire, etc. Exact subcommands follow vanilla `/team` help.

---

## Teleporting and homes

`/tp` — Move players around. With permission you can teleport yourself to someone, someone to you, or one player to another.

`/tpa`, `/tpahere`, `/tpaccept`, `/tpacancel`, `/tpask` — Player teleport *requests*: ask to go to someone, ask them to come to you, accept or cancel.

`/minecraft:tp` (and other `/minecraft:…` commands) — Same as the normal command; the `minecraft:` prefix is just the vanilla namespace.

`/home`, `/sethome`, `/delhome`, `/homes` — Save a location and warp back. Names like `base` or `farm` are whatever the player chose.

`/warp`, `/warps`, `/spawn` — Warp to a fixed point an admin created, list warps, or go to spawn.

`/rtp`, `/betterrtp` — Random teleport into the world using that plugin’s rules (which worlds, cooldowns, safe spots).

---

## Economy and trading

Servers hook economy into **Vault**; the commands below are the usual shapes (exact wording can differ slightly per plugin).

`/pay`, `/balance`, `/bal`, `/money` — Pay another player or check balances.

`/baltop`, `/balancetop` — Richest players list.

`/eco` — Staff-only: give, take, or set a player’s balance.

`/ah` — Auction house: list items for sale or buy from a shared menu.

`/sell`, `/sellgui` — Sell items to the server’s buy shop (command or GUI).

`/trade` — Opens a trade window with another player so neither can scam the other mid-exchange.

`/coinflip` — Challenge someone to a wager; one side wins the pot.

`/tebex` — Tied to **Tebex** (Buycraft): web store purchases and packages.

---

## Extra chests and inspecting gear

`/pv`, `/vault`, … — **Player vaults**: extra pages of storage beyond the inventory. Number often means page (`/pv 3`). Admins may open another player’s vault with permission.

`/ec` — Open your ender chest remotely; staff builds sometimes add opening someone else’s.

`/invsee` — Staff views (and on many setups edits) another player’s live inventory.

---

## WorldEdit (`//…`)

Bulk editing: select an area, then run operations. Often used with **FastAsyncWorldEdit (FAWE)**; players still type `//` the same way. `/fawe reload` reloads that plugin’s config.

Common pieces:

- `//wand`, `//pos1`, `//pos2` — Selection tool or corners.
- `//set`, `//replace` — Fill the selection with blocks or swap one block type for another.
- `//copy`, `//paste`, `//undo` — Clipboard and undo.
- `//schem save`, `//schem load` — Save/load a schematic file.
- `//brush …` — Paint terrain with a brush bound to a tool.
- `//setbiome` — Change biome inside the selection.

Official command list: [WorldEdit docs](https://worldedit.enginehub.org/en/latest/commands/).

---

## WorldGuard (`/rg`)

Protects areas (**regions**) and sets rules (**flags**) per region.

Examples:

```
/rg define spawn          Create region "spawn" from your current selection (after using WE wand).
/rg flag spawn pvp deny   Turn off PvP in that region.
/rg flag spawn build deny Stop block place/break for people without bypass (exact flags depend on version).
/rg addmember spawn g:builders   Let members of the "builders" group build there.
/rg priority shop 10     When two regions overlap, higher priority wins.
/rg info spawn            Show flags and members.
/rg reload                Reload WorldGuard configs from disk.
```

`/rg flag <region> <flag> <allow|deny>` always means: “for this region, set this rule.” Full flag list: [WorldGuard commands](https://worldguard.enginehub.org/en/latest/regions/commands/).

---

## Vanilla admin-style building

`/fill`, `/setblock`, `/clone` — Fill a box with blocks, set one block, or copy a volume. Need cheats/op and correct coordinates and block ids.

---

## Chunk pregeneration

`/chunky …` — **Chunky** plugin: generates chunks ahead of time so players don’t hit lag when they explore. Subcommands follow `/chunky help` on the server.

---

## LuckPerms

`/lp …` — Permissions: groups, tracks, user nodes, temporary permissions. `/lp editor` opens the web editor; after saving there you run the `/lp applyedits …` line it gives you.

Docs: [LuckPerms wiki](https://github.com/LuckPerms/LuckPerms/wiki/Command-Usage).

---

## TAB (tab list / nametags / scoreboard)

`/tab reload` — Reload TAB config after you edit files. Other `/tab …` lines depend on how scoreboards and layouts are named in config.

Wiki: [TAB](https://github.com/NEZNAMY/TAB/wiki).

---

## PlaceholderAPI

`/papi …` — Downloads or lists **placeholder** expansions used in scoreboards, chat, and menus (e.g. economy balance placeholders).

---

## DeluxeMenus

`/deluxemenu open <menu>` — Opens a GUI defined in that plugin’s YAML. `/deluxemenu reload` reloads configs.

---

## CoreProtect

`/co …` or `/coreprotect …` — Logs block changes; staff use it for grief checks.

- Inspect mode — Click blocks to see who changed them.
- Lookup — Search who did what in an area and time range.
- Rollback — Undo those changes.
- Restore — Undo a rollback.

Docs: [CoreProtect commands](https://docs.coreprotect.net/commands/).

---

## Moderation and broadcast

`/ban`, `/unban`, `/tempban`, `/kick` — Remove or block players from the server.

`/mute`, `/unmute`, `/tempmute` — Stop a player from chatting.

`/warn`, `/warnlist` — Strike systems on plugins that support warnings.

`/ipban`, `/banip` — Ban by IP address.

`/litebans` — Admin interface for **LiteBans** when that plugin is installed.

`/alts` — Used by alt-detection plugins to tie accounts together (depends on the plugin).

`/broadcast`, `/announce` — Message every online player (usually colored).

`/sudo <player> <command>` — Runs a command as if that player typed it. Very powerful.

`/op`, `/deop` — Grant or remove vanilla **operator** on the server.

---

## Simple Voice Chat

`/voicechat …`, `/vcban`, `/unvcban` — Voice chat plugin controls; bans target voice, not normal chat.

---

## Inventory snapshots (rollback)

`/irp …` — **Inventory Rollback Plus**: backups around death/quit/etc.; staff restores inventories through menus. [Spigot resource](https://www.spigotmc.org/resources/inventory-rollback-plus-1-8-1-21-11.85811/).

---

## NPCs, disguise, holograms

`/npc …` — Typical of **Citizens** or similar NPC plugins (create/move NPCs, skins, etc.).

`/disguise …` — **LibsDisguises** pattern: look like another mob or player model.

`/nickname` / `/nick` — Change display name (often Essentials-style plugins).

`/fholo …` — **FancyHolograms**: floating text lines in the world.

---

## Performance and server internals

`/spark …` — **Spark** profiler for CPU and lag.

`/paper …` — Paper-specific utilities (version, watchdog, etc.); see `/paper` help on the server.

`/plugman …` — Loads, unloads, or reloads plugins without a full restart. Easy to break production worlds; restarts are safer.

`/matrix …` — **Matrix** anticheat admin commands.

`/skript …` — **Skript**: custom scripts define extra commands; behavior is whatever that server’s scripts say.

---

## Worlds and shops

`/mv`, `/mvtp`, … — **Multiverse**-style world management and teleports between worlds.

`/shopkeepers …` — **Shopkeepers** NPC merchant plugin.

`/discord`, `/discordannounce` — Often **DiscordSRV** or similar: link accounts or send announcements to Discord.

---

## Vanilla goodies ops use a lot

`/effect`, `/enchant`, `/give`, `/summon`, `/kill`, `/damage`, `/attribute` — Apply effects, enchant held items, give items, spawn entities, kill selectors, apply damage types, tweak attributes. Syntax matches the Minecraft version the server runs.

`/gamemode` (`/gm`, `/gmc`, `/gms`, `/gmsp`, …) — Survival, creative, spectator, adventure.

`/time`, `/weather` — World time and weather.

`/execute` — Chains vanilla subcommands (runs as/at/position); powerful but verbose.

`/rules`, `/help`, `/helpop`, `/version`, `/plugins` — Info pages or listing installed plugins.

---

## Who shouldn’t get what

`/sudo`, `/op`, `/eco`, WorldEdit, WorldGuard region bypass, CoreProtect rollback, `/invsee`, and `/lp` can wreck balances or terrain fast. Hand those perms to people you trust and treat mistakes as serious.

---

## Further reading

- [WorldEdit](https://worldedit.enginehub.org/en/latest/commands/)
- [WorldGuard regions](https://worldguard.enginehub.org/en/latest/regions/commands/)
- [CoreProtect](https://docs.coreprotect.net/commands/)
- [LuckPerms](https://github.com/LuckPerms/LuckPerms/wiki/Command-Usage)
- [TAB](https://github.com/NEZNAMY/TAB/wiki)
- [InteractiveChat](https://hangar.papermc.io/LOOHP/InteractiveChat)
- [Inventory Rollback Plus](https://www.spigotmc.org/resources/inventory-rollback-plus-1-8-1-21-11.85811/)
