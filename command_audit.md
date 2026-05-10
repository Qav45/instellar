# What these commands are

Logs came off your Bloom box (`/logs` on SFTP, saved under `mc_server_logs/`). Any line that looked like someone ran a command (`issued server command:` in the log) got scraped. Identical lines were merged once, so you get **8,062** different command strings total, from **everyone** who played—not just staff.

The list lives in `_issued_commands_all_players.txt` next to this file if you want to search it yourself.

**Quick numbers:** those 8k strings boil down to about **1,360** different “roots” (the first word after the slash, or `//` for WorldEdit). Most of the noise is the same few plugins with tons of arguments—especially pm-style commands, economy, and InteractiveChat hashes.

---

## How to read this doc

Commands are grouped by what they’re *for*, not alphabetically. If something sounds unfamiliar, it’s probably renamed on your server—run `/plugins` in-game or peek at the JAR list.

---

## Chat, PMs, and items in chat

**`/whisper`** — Private message. Same idea as `/msg` or `/tell` on a lot of servers. Logs can show huge lines because the whole message is one “command.”

Examples (shape only—names/text are yours):

```
/whisper Steve hey can you help at spawn
/msg Steve same idea different command
```

**`/interactivechat`** — People share items, invs, or ender chests in chat; others click and open a **read-only** preview. You’ll see lots of `viewitem`, `viewinv`, `viewender` plus a long ID—that’s normal.

Example:

```
/interactivechat viewitem a1b2c3d4e5f6...
```

**`/team`** / **`/teammsg`** — Vanilla scoreboard teams (tags, who can hit whom, etc.). Often tangled up with minigames or PvP plugins.

**`/venturechat`** — Extra chat channels / formatting, depending how you set it up.

---

## Teleports and homes

**`/tp`**, **`/tpa`**, **`/tpahere`**, **`/tpaccept`**, **`/tpacancel`**, **`/tpask`** — The usual dance: staff teleport, player asks to TP, “bring them here,” accept/cancel. Often Essentials or close enough.

Examples:

```
/tp Steve              ← you teleport to Steve (if you have perms)
/tp Steve Alex         ← teleport Steve to Alex
/tpa Steve             ← ask Steve if you can TP to them
/tpahere Steve         ← ask Steve to TP to you
/tpaccept              ← accept a pending request
/tpacancel             ← cancel yours or deny incoming
```

**`/minecraft:`…`** — Same as vanilla commands, just written with the namespace (e.g. `minecraft:tp`).

```
/minecraft:tp Steve Alex
```

**`/home`**, **`/sethome`**, **`/delhome`**, **`/homes`**, **`/createhome`** — Save spots and warp back. Classic Essentials-style stuff.

Examples:

```
/sethome base          ← save “base” at your feet
/home base             ← go there
/delhome base          ← delete that home
/homes                 ← list names
```

**`/warp`**, **`/warps`**, **`/spawn`** — Public warps and spawn.

```
/warp shop
/warps
/spawn
```

**`/betterrtp`**, **`/rtp`** — Random teleport into the world with whatever rules you configured.

```
/rtp
/betterrtp world world
```

---

## Money and shops

**`/pay`**, **`/bal`**, **`/balance`**, **`/money`**, **`/baltop`**, **`/balancetop`** — Check balance, send cash, look at the rich list. Hooks into Vault + whatever economy plugin you run.

Examples:

```
/pay Steve 5000
/bal Steve
/balance
/baltop 10
```

**`/eco`** — Staff moving money around (give / take / set). Powerful; worth restricting.

Examples (syntax varies slightly by plugin—same idea):

```
/eco give Steve 10000
/eco take Steve 5000
/eco set Steve 0
```

**`/ah`** — Auction house GUI.

```
/ah                  ← open listings
/ah sell 10000       ← list held item for price (example shape)
```

**`/sell`**, **`/sellgui`**, **`/sellg`** — Sell items to the server shop.

```
/sell                ← often sells what you’re holding
/sellgui             ← opens sell GUI if your plugin uses it
```

**`/trade`** — Safe trade window between two players.

```
/trade Steve
```

**`/coinflip`**, **`/cf`** — Betting another player; `cf` might be a short alias for coinflip or something else—your logs have both.

```
/coinflip challenge Steve 1000
/coinflip accept
```

**`/refined`** — Looks like a **second currency** or physical “notes” style money (`withdraw`, amounts). Name comes from whatever plugin you installed.

**`/tokens`**, **`/token`** — Usually a separate token currency (battle pass, crate currency, etc.). Check which plugin owns it.

**`/tebex`** — Store / Buycraft style integration.

**`/loanrequest`** — Loans—almost certainly a custom or banking plugin.

---

## Storage and items

**`/pv`**, **`/vault`**, **`/vaults`**, **`/vaultadmin`**, **`/vaultsadmin`** — Extra chest pages (“playervaults”). Admin forms open or wipe other people’s pages depending on perms.

Examples:

```
/pv              ← open vault menu or default page
/pv 3            ← open page 3
/pv Steve 2      ← staff: peek Steve’s page 2 (if allowed)
/vaultadmin reload   ← example admin reload (exact label depends on plugin)
```

**`/ec`** — Open ender chest without standing at one (sometimes other people’s, if staff).

```
/ec
/ec Steve
```

**`/invsee`** — Staff looking at (and maybe editing) someone’s live inventory.

```
/invsee Steve
```

**`/ie`**, **`/itemedit`** — Tweak item name, lore, flags from in-game—handy for events, easy to abuse.

**`/compress`**, **`/autopickup`**, **`/autosmelt`**, **`/axboosters`** — Quality-of-life: compress stacks, auto pickup, auto smelt, booster keys—whatever your pack adds.

---

## Building and worlds

**WorldEdit / FAWE** — the big `//` commands (`//set`, `//replace`, `//paste`, `//brush`, `//undo`, shapes, biomes, etc.). Bulk terrain and block edits. `/fawe reload` reloads that side of things. Big selections can still lag or eat RAM—same as always.

Typical flow—you select a box with the wand (or `//pos1` / `//pos2`), then run an op:

```
//wand                   ← get selection axe (if enabled)
//pos1                   ← corner A
//pos2                   ← corner B
//set stone              ← entire selection becomes stone
//replace dirt grass_block
//paste                  ← paste clipboard at your feet
//undo                   ← step back one edit
//setbiome plains        ← biome inside selection
```

**`/schem`**, **`/worldedit`** — Schematics and WorldEdit admin/help style commands.

```
//schem load shopbuild
//schem save myspawn
```

**`/rg`** — **WorldGuard**: cuboid **regions** + **flags**. A flag is just “for this region, allow or deny something.” Your logs had tons of `ironore`, `diamondblock`, etc.—same idea, different region names.

Examples:

```
/rg define spawn               ← after selecting with wand: creates region “spawn”
/rg create farm cornfield      ← some setups use create/add differently—same purpose

/rg flag spawn pvp deny        ← no PvP inside “spawn”
/rg flag spawn build deny      ← guests can’t place/break blocks
/rg flag spawn mob-spawning deny ← fewer/natural mobs (exact flag names depend on WG version)

/rg addmember spawn g:builders ← members group can build there
/rg addowner spawn Steve       ← Steve owns the region

/rg priority farm 10           ← higher number wins when regions overlap
/rg info spawn                 ← dump flags + members
/rg reload                     ← reload WG configs from disk
```

So **`/rg flag`** isn’t magic by itself—it always means “change one behavior flag on a named region.” First argument after `flag` is the region, then the flag name, then usually allow/deny (or a value).

**`/fill`**, **`/setblock`**, **`/clone`** (if present) — Vanilla bulk building at coords.

```
/fill ~ ~ ~ ~10 ~10 ~10 minecraft:air replace minecraft:stone
/setblock ~ ~-1 ~ minecraft:bedrock
```

**`/chunky`** — Pregenerates chunks so the world doesn’t stutter when players explore.

```
/chunky start world
/chunky pause
```

---

## Permissions, tab list, placeholders

**`/lp`** — **LuckPerms**. Groups, tracks, temp perms, verbose mode. **`/lp editor`** opens the web UI; you paste a command back to apply edits.

Examples:

```
/lp user Steve parent set vip
/lp user Steve permission set some.plugin.perk true
/lp group vip meta setprefix "&a[VIP] "
/lp editor                       ← opens browser session
/lp applyedits <paste from browser>
```

**`/tab`** — Tab list, nametags, scoreboards. **`/tab reload`** after you edit configs.

Examples (TAB plugin—exact subcommands match your YAML):

```
/tab reload
/tab scoreboard show pvp Steve     ← show scoreboard named “pvp” to Steve
/tab nametag preview               ← depends on version; idea is “see nametag layout”
```

**`/papi`**, **`/placeholderapi`** — PlaceholderAPI: pull expansions from the cloud, wire placeholders into TAB, menus, chat.

```
/papi ecloud download Vault
/papi list                       ← often lists expansions (syntax varies)
```

**`/deluxemenu`** — Opens menu GUIs from config (`open …`).

```
/deluxemenu open storage
/deluxemenu reload
```

---

## Grief checks and rollbacks

**`/co`**, **`/coreprotect`**, sometimes **`/core`** — **CoreProtect**: click blocks to see history, search who broke what, roll back or restore. Main staff tool for grief.

Examples:

```
/co inspect                      ← toggle: left/right-click blocks for who touched them
/co lookup u:Steve t:1h r:20      ← “what did Steve do in last hour within 20 blocks”
/co rollback u:Griefer t:30m r:50
/co restore u:Builder t:2h r:10    ← opposite of rollback—put changes back
/co near                         ← shorthand lookup near you
```

Think of it as three verbs: **inspect** (click mode), **lookup** (search log), **rollback** / **restore** (undo redo).

---

## Moderation

**`/ban`**, **`/unban`**, **`/tempban`**, **`/ipban`**, **`/banip`** — Ban toolkit, including IP and timed bans.

```
/ban Steve griefing
/tempban Steve 7d language
/unban Steve
/banip 203.0.113.50 VPN abuse
```

**`/mute`**, **`/unmute`**, **`/tempmute`** — Chat mutes.

```
/mute Steve
/tempmute Steve 30m caps spam
/unmute Steve
```

**`/warn`**, **`/unwarn`**, **`/warnlist`** — Warning strikes.

```
/warn Steve harassment
/warnlist Steve
```

**`/kick`** — Boot someone offline.

```
/kick Steve please re-read /rules
```

**`/litebans`** — If you see this root, LiteBans (or similar) is probably in the mix.

**`/alts`** — Alt / linked-account style lookups.

```
/alts Steve
```

**`/broadcast`**, **`/announce`** — Loud server-wide messages (usually staff).

```
/broadcast Server reboot in 5 minutes
```

**`/sudo`** — Run a command *as* another player. Very strong.

```
/sudo Steve spawn          ← runs /spawn as Steve
```

**`/op`**, **`/deop`** — Vanilla operator flag. Also very strong.

```
/op Steve
/deop Steve
```

---

## PvP, events, voice

**`/tournament`**, **`/specmatch`**, **`/ragekoth`**, **`/ffa`**, **`/combattag`**, **`/pvp`**, **`/pvpmanager`**, **`/pvpstatus`** — Event and PvP plugins: brackets, spectating, KOTH-style zones, combat tags, etc. Exact behavior = your configs.

Example shapes (names change per plugin):

```
/combattag Steve 30              ← example: tag player for 30s “in combat”
/pvpmanager reload
```

**`/voicechat`**, **`/vcban`**, **`/unvcban`** — Voice chat plugin; bans are for voice, not Minecraft chat.

```
/voicechat invite Steve          ← depends on plugin build
/vcban Steve 1d mic spam
/unvcban Steve
```

---

## Gameplay that looks custom on your server

**`/instellar`** (and `instellar:…` variants) — Your own progression / gear / dialogue / zone stuff from logs—not one universal public plugin with a single manual. If you need docs, they’re in that plugin’s config or dev page.

**`/meg`** — Shows up as utility-style commands (reload, mass kills, etc.). Treat as part of your stack until you match it to a JAR name.

**`/zonebooster`**, **`/boost`** — Timed multipliers (drops, XP, whatever you wired). Server-specific.

**`/welcome`** — New-player flow / rewards (sometimes tied to crates).

**`/killall`** — Wipes entity types in bulk. Easy to aim wrong.

**`/timeblades`** — Didn’t map cleanly to a well-known public plugin; probably custom or niche—check your plugin folder.

**`/keepinventoryzones`** — Per-area keep-inventory rules (PvP vs safe zones).

**`/replay`** — Recording / replay for investigations (plugin-dependent).

**`/forge`** — Often someone typing “Forge” on a Paper server by habit, or a custom command named that—context in the raw log line helps.

**`/login`** — Usually an **auth** plugin (password on join) if you’re offline-mode or behind a certain proxy setup.

---

## NPCs, disguises, misc admin

**`/npc`** — Citizens / FancyNPCs / similar: NPCs, skins, teleport, dialogue hooks.

**`/disguise`** — Look like a mob or another player (LibsDisguises-type).

**`/nickname`** — Display name changes.

**`/dialogue`** — NPC conversation flows.

**`/fholo`** — Fancy holograms (floating text, edits, copy, etc.).

```
/fholo create text WelcomeLine
/fholo edit WelcomeLine setline 1 &aWelcome
/fholo edit WelcomeLine moveHere
```

**`/spark`** — Profiler: see what’s eating CPU when the server dips.

**`/paper`** — Paper’s own debug / dump style commands (depends what you type after it).

**`/plugman`** — Load/unload plugins on the fly. Handy in a pinch, risky on a live server—restarts are safer.

**`/matrix`** — Matrix anticheat admin.

**`/skript`** — Skript: custom scripted commands and logic.

**`/irp`** — Matches **Inventory Rollback Plus** pretty well (backups, restore menus). There’s also a bit of `/inventoryrollback` in the logs—could be another plugin or an alias.

```
/irp restore Steve               ← open backup browser for Steve
/irp reload
```

**`/damage`** — Vanilla damage to entities.

```
/damage Steve 6 minecraft:player_attack
```

**`/effect`**, **`/enchant`**, **`/give`**, **`/summon`**, **`/kill`**, **`/attribute`** — Creative / admin vanilla toolbox.

```
/effect give Steve speed 30 1 true
/enchant Steve sharpness 5
/give Steve diamond 64
/summon zombie ~ ~ ~
/kill @e[type=item,distance=..10]
```

**`/rules`**, **`/help`**, **`/helpop`**, **`/version`**, **`/ver`**, **`/plugins`** — Info and “call staff” style commands.

**`/discord`**, **`/discordannounce`** — Discord bridge (DiscordSRV-type): linking, announcements.

**`/shopkeepers`**, **`/shopgui`**, **`/auction`**, **`/zauction`** — NPC shops, GUI shops, auction variants.

**`/fish`** — Fishing plugin / event commands.

**`/is`** — Often skyblock “island” when people shorten it.

**`/mv`**, **`/mvtp`** — Multiverse-style world jumps if you use it.

**`/join`**, **`/profile`**, **`/joinleave`** — Join messages or profile UIs—depends on your pack.

**`/t`** — Too generic to guess without the rest of the line; could be tempban, team, or a plugin alias.

---

## WorldEdit vs FAWE

FAWE sits under WorldEdit and speeds up big edits. Players still type `//` the same way. Either way, give WorldEdit perms only to people you trust with world paint.

---

## Perms worth locking down

Anyone with **`/sudo`**, **`/op`**, **`/eco`**, rollback commands, WorldEdit, **`/invsee`**, or **`/lp`** can do a lot of damage—accidentally or on purpose. **`/plugman`** is in the same bucket.

Logs only prove someone *typed* the command; they don’t show whether it was wrong click, joke, or policy-approved.

---

## Links when you want official wording

- [WorldGuard regions & flags](https://worldguard.enginehub.org/en/latest/regions/commands/) — fuller `/rg flag` list than we pasted here
- [CoreProtect commands](https://docs.coreprotect.net/commands/)
- [TAB scoreboards](https://github.com/NEZNAMY/TAB/wiki/Feature-guide:-Scoreboard)
- [LuckPerms web editor](https://github.com/LuckPerms/LuckPerms/wiki/Web-Editor)
- [InteractiveChat](https://hangar.papermc.io/LOOHP/InteractiveChat)
- [WorldEdit commands](https://worldedit.enginehub.org/en/latest/commands/)
- [Inventory Rollback Plus](https://www.spigotmc.org/resources/inventory-rollback-plus-1-8-1-21-11.85811/)
- [PlayerVaultsX (example `/pv` plugin)](https://github.com/westkevin12/PlayerVaultsX)

---

## SFTP script note

`download_sftp_logs.py` reads the password from the environment (`SFTP_PASSWORD`), not from the file—don’t commit passwords to git.