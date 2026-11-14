# aka

<p align="center">
  <b>Dynamic Nickname, Rank Disguise, and Custom Skin Engine</b>
  <br />
  <i>Created and Developed by <b>Krishna Mittal</b> • All Rights Reserved</i>
  <br />
  <i>Engineered for Paper, Purpur, Folia, and Spigot - Compatible from <b>Minecraft 1.20 up to 26.3</b>!</i>
  <br /><br />
  <img src="https://img.shields.io/badge/Author-Krishna_Mittal-00d2ff?style=for-the-badge" alt="Author Krishna Mittal" />
  <img src="https://img.shields.io/badge/Rights-All_Rights_Belong_To_Krishna_Mittal-blueviolet?style=for-the-badge" alt="All Rights Belong To Krishna Mittal" />
  <img src="https://img.shields.io/badge/Minecraft-1.20_to_26.3-2ea44f?style=for-the-badge&logo=minecraft&logoColor=white" alt="Minecraft Version" />
  <img src="https://img.shields.io/badge/Platform-Paper_%7C_Purpur_%7C_Folia-e67e22?style=for-the-badge" alt="Platform Paper Purpur Folia" />
  <img src="https://img.shields.io/badge/Java-17_%7C_21-007acc?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java Runtime" />
  <img src="https://img.shields.io/badge/License-All_Rights_Reserved-9b59b6?style=for-the-badge" alt="All Rights Reserved License" />
</p>

---

> 🏆 **Engineered for Content Creators & High-Traffic Servers:** **aka** gives YouTubers, streamers, and staff members complete privacy when playing on public servers. Disguise your name, skin, overhead nametag, tab list presence, and LuckPerms rank prefix with a single command — with zero risk of broken inventories or cracked server auth issues.
>
> 💬 **Discord Support:** Reach out anytime on Discord to **`@kzen_fights`** (User ID: `1275335096924373032`) for questions, assistance, or feature suggestions!

---

## 🛡️ Overview

Many content creators and server administrators cannot play casually without being chased, targeted, or stream-sniped. **aka** provides a robust, seamless disguise engine and full-featured **SkinRestorer** that manages:
- **Player Nicknames & Disguises** (custom names or random generator)
- **Built-in SkinsRestorer Engine** (automatically restores official Mojang skins for offline/cracked servers on join)
- **Famous Creator Presets** (instant one-click skins for ClownPierce, Technoblade, Dream, Camman18, and more)
- **Custom Skin URLs & Uploads** (signed on-the-fly via Mineskin API without client mods)
- **TAB List Formatting** (Adventure Component rendering)
- **Overhead NameTag** (Scoreboard teams with disguised prefixes)
- **Chat Formatting** (Native Adventure `AsyncChatEvent` + legacy fallback)
- **Death Messages** (Replaces real names with nicknames)
- **LuckPerms Rank Disguise** (Masks `[YouTuber]` / `[Admin]` prefixes as standard `[Member]` or `&7`)

---

## 🔒 Cracked Server & AuthMe Protection

Most nickname plugins break cracked/offline-mode servers and authentication plugins (**AuthMeReloaded**, **nLogin**, **FastLogin**) because they alter the player's underlying UUID, causing lost inventories, cleared ender chests, or repeat `/login` loops.

**aka guarantees complete data and session safety:**
1. **Strict UUID Preservation:** The player's network UUID (`player.getUniqueId()`) is **NEVER** modified. All server stats, inventories, advancements, and database records remain 100% intact.
2. **Account Hijacking & Impersonation Defense:** Blocks users from nicking as any account registered in AuthMe, nLogin, or existing on disk.
3. **Pre-Login Enforcement:** Requires unauthenticated players to complete `/login` or `/register` before executing any disguise commands.

---

## 🎮 Multi-Version & Platform Compatibility

Pre-compiled builds are available to match your server runtime:
* 🟢 **Minecraft 1.20 Series (`1.20` – `1.20.6`):**
  * Java Runtime: **Java 17 LTS+**
  * Recommended Build: `aka-1.0.0-Java17.jar`
* 🟢 **Minecraft 1.21 Series (`1.21` – `1.21.4+`):**
  * Java Runtime: **Java 21 LTS+**
  * Recommended Build: `aka-1.0.0-Java21.jar` / `aka-1.0.0.jar`
* 🟢 **Modern & Future Versions (`1.21.x` – `26.3`):**
  * Java Runtime: **Java 21 LTS+**
  * Recommended Build: `aka-1.0.0.jar`

**Supported Platforms:** Paper, Purpur, Folia (with universal `PlatformScheduler` support), and Spigot.

---

## 🌐 Third-Party Services Disclosure (Modrinth & CurseForge Compliance)

To provide skin signing without requiring client-side mods, **aka** connects to two external endpoints:
1. **Mojang API (`https://api.mojang.com` / `https://sessionserver.mojang.com`):** Used to retrieve texture values and signatures when a player requests a Minecraft username skin (`/skin <player>`).
2. **Mineskin API (`https://api.mineskin.org`):** Used strictly to upload custom PNG image URLs or files and obtain official Mojang cryptographic signatures so clients can render custom skins.

* **Privacy & Data Security:** No player credentials, server IPs, hardware IDs, or personal information are ever collected, stored, or transmitted.
* **Opt-Out:** Server administrators can disable all external network skin requests by setting `skins.enabled: false` in `plugins/aka/config.yml`.

---

## ⚡ Commands & Permissions

| Command | Permission | Description |
| :--- | :--- | :--- |
| `/nick <name\|random>` | `aka.use` | Change your nickname or pick a random disguise |
| `/nick <name> [player]` | `aka.others` | Change another player's nickname (Staff) |
| `/unnick` | `aka.use` | Restore your original identity and skin |
| `/unnick [player]` | `aka.others` | Clear another player's nickname (Staff) |
| `/skin <player\|url\|clear\|update>` | `aka.skin` | Change, reset, or refresh your skin (SkinsRestorer compatible) |
| `/skin set <player>` | `aka.skin` | SkinsRestorer-compatible skin setting |
| `/skin clear` / `/skin reset` | `aka.skin` | Clear custom skin & restore original/Mojang skin |
| `/skin update` | `aka.skin` | Force refresh your skin from Mojang session servers |
| `/skins` / `/skin menu` | `aka.skin` | Open the interactive Skin Wardrobe GUI |
| `/skin <...> [player]` | `aka.others` | Change another player's skin (Staff) |
| `/sr <reload\|set\|clear\|status>` | `aka.admin` | Administrative SkinsRestorer drop-in commands |
| `/realname <nickname>` | `aka.realname` | Look up the real identity of a disguised player |
| `/aka list` | `aka.admin` / `aka.realname` | View all active disguises, real names, and ranks |
| `/aka reload` | `aka.admin` | Reload configuration, messages, and skin cache |

### Permission Hierarchy
- `aka.*`: Full access to all plugin features.
- `aka.admin`: Administrative control (`/aka reload`, `/aka list`, `/realname`).
- `aka.use`: Permission to nickname oneself (assign to YouTuber / Media group).
- `aka.skin`: Permission to change skin.
- `aka.skin.url`: Permission to use external image URLs.
- `aka.color`: Permission to use colors (`&a`, `&l`, `&#HEX`) in nicknames.
- `aka.others`: Permission to manage disguises for other players.
- `aka.realname`: Permission to uncover disguised players.
- `aka.bypass.blacklist`: Permission to bypass name blacklist.

---

## 🎬 YouTuber Setup Guide (LuckPerms)

To allow YouTubers to disguise their identity and conceal their `[YouTuber]` prefix:

```bash
# Grant disguise permissions to the YouTuber rank
/lp group youtuber permission set aka.use true
/lp group youtuber permission set aka.skin true
```

In `plugins/aka/config.yml`:
```yaml
luckperms:
  enabled: true
  disguise-rank: true
  default-disguise-prefix: '&7'
  rank-disguises:
    youtuber: 'default'
    media: 'default'
```

When a YouTuber enters `/nick random`, their name changes to a realistic player identity, their skin updates automatically, and their prefix becomes `&7` (regular member), allowing them to play uninterrupted.

---

## 🔨 Building from Source

To compile the project:
```powershell
.\build.ps1
```
This automatically produces bytecode for both **Java 17** and **Java 21** inside `releases/` and `target/`.

---

## 📄 License & Copyright

**Proprietary Software — All Rights Reserved.**  
Copyright (c) 2026 **Krishna Mittal**.  
All rights, title, and intellectual property belong exclusively to Krishna Mittal.
