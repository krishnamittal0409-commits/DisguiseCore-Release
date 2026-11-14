# DisguiseCore

<p align="center">
  <b>Dynamic Nickname, Rank Disguise, and Universal Skin Engine</b>
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

> 🏆 **Engineered for Content Creators & High-Traffic Server Networks:** **DisguiseCore** gives YouTubers, streamers, and staff members complete privacy when playing on public servers. Disguise your name, skin, overhead nametag, tab list presence, and LuckPerms rank prefix with a single command — with zero risk of broken inventories or cracked server auth issues.
>
> 💬 **Discord Support:** Reach out anytime on Discord to **`@kzen_fights`** (User ID: `1275335096924373032`) for questions, assistance, or feature suggestions!

---

## 🛡️ Overview

Many content creators and server administrators cannot play casually without being chased, targeted, or stream-sniped. **DisguiseCore** provides a robust, seamless disguise engine and full-featured **Universal SkinRestorer** that manages:
- **Player Nicknames & Disguises** (custom names or random generator)
- **Universal SkinsRestorer Engine** (automatically restores official Mojang skins for offline/cracked servers on join)
- **Cracked Launcher Auto-Resolution** (automatically detects skins from TLauncher, FastClient, SKlauncher, Ely.by, and LittleSkin)
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

**DisguiseCore guarantees complete data and session safety:**
1. **Strict UUID Preservation:** The player's network UUID (`player.getUniqueId()`) is **NEVER** modified. All server stats, inventories, advancements, and database records remain 100% intact.
2. **Account Hijacking & Impersonation Defense:** Blocks users from nicking as any account registered in AuthMe, nLogin, or existing on disk.
3. **Pre-Login Enforcement:** Requires unauthenticated players to complete `/login` or `/register` before executing any disguise commands.

---

## 🎮 Multi-Version & Platform Compatibility

Pre-compiled builds are available to match your server runtime:
* 🟢 **Minecraft 1.20 Series (`1.20` – `1.20.6`):**
  * Java Runtime: **Java 17 LTS+**
  * Recommended Build: `DisguiseCore-1.0.0-Java17.jar`
* 🟢 **Minecraft 1.21 Series (`1.21` – `1.21.4+`):**
  * Java Runtime: **Java 21 LTS+**
  * Recommended Build: `DisguiseCore-1.0.0-Java21.jar` / `DisguiseCore-1.0.0.jar`
* 🟢 **Modern & Future Versions (`1.21.x` – `26.3`):**
  * Java Runtime: **Java 21 LTS+**
  * Recommended Build: `DisguiseCore-1.0.0.jar`

**Supported Platforms:** Paper, Purpur, Folia (with universal `PlatformScheduler` support), and Spigot.

---

## 🌐 Third-Party Services Disclosure (Modrinth & CurseForge Compliance)

To provide skin signing and universal cracked launcher compatibility (TLauncher, FastClient, SKlauncher, Ely.by, LittleSkin) without requiring client-side mods, **DisguiseCore** connects to external skin endpoints:
1. **Mojang API (`https://api.mojang.com` / `https://sessionserver.mojang.com`):** Used to retrieve official texture values and signatures when resolving premium Minecraft accounts.
2. **Cracked Skin Networks (`auth.tlauncher.org`, `skinsystem.ely.by`, `littleskin.cn`):** Used to detect and retrieve custom skins uploaded on TLauncher, Ely.by, FastClient, and CustomSkinLoader/BlessingSkin networks.
3. **Mineskin API (`https://api.mineskin.org`):** Used strictly to upload custom PNG image URLs or files and obtain official Mojang cryptographic signatures so clients can render custom skins.

* **Privacy & Data Security:** No player credentials, server IPs, hardware IDs, or personal information are ever collected, stored, or transmitted.
* **Opt-Out:** Server administrators can disable all external network skin requests by setting `skins.enabled: false` in `plugins/DisguiseCore/config.yml`.

---

## ⚡ Commands & Permissions

| Command | Permission | Description |
| :--- | :--- | :--- |
| `/nick <name\|random>` | `disguisecore.use` | Change your nickname or pick a random disguise |
| `/nick <name> [player]` | `disguisecore.others` | Change another player's nickname (Staff) |
| `/unnick` | `disguisecore.use` | Restore your original identity and skin |
| `/unnick [player]` | `disguisecore.others` | Clear another player's nickname (Staff) |
| `/skin <player\|url\|clear\|update>` | `disguisecore.skin` | Change, reset, or refresh your skin (SkinsRestorer compatible) |
| `/skin set <player>` | `disguisecore.skin` | SkinsRestorer-compatible skin setting |
| `/skin clear` / `/skin reset` | `disguisecore.skin` | Clear custom skin & restore original/Mojang skin |
| `/skin update` | `disguisecore.skin` | Force refresh your skin from Mojang session servers |
| `/skins` / `/skin menu` | `disguisecore.skin` | Open the interactive Skin Wardrobe GUI |
| `/skin <...> [player]` | `disguisecore.others` | Change another player's skin (Staff) |
| `/sr <reload\|set\|clear\|status>` | `disguisecore.admin` | Administrative SkinsRestorer drop-in commands |
| `/realname <nickname>` | `disguisecore.realname` | Look up the real identity of a disguised player |
| `/dc list` / `/disguisecore list` | `disguisecore.admin` | View all active disguises, real names, and ranks |
| `/dc update [check\|info]` | `disguisecore.admin` | Check for updates and view release changelog |
| `/dc reload` / `/disguisecore reload` | `disguisecore.admin` | Reload configuration, messages, and skin cache |
| `/dc` / `/disguisecore` | `disguisecore.gui` | Open the master interactive GUI Dashboard |

### Permission Hierarchy
- `disguisecore.*`: Full access to all plugin features.
- `disguisecore.admin`: Administrative control (`/dc reload`, `/dc list`, `/realname`, `/sr`).
- `disguisecore.use`: Permission to nickname oneself (assign to YouTuber / Media group).
- `disguisecore.skin`: Permission to change skin.
- `disguisecore.skin.url`: Permission to use external image URLs.
- `disguisecore.skin.bypasscooldown`: Bypass anti-spam skin changing cooldown.
- `disguisecore.color`: Permission to use colors (`&a`, `&l`, `&#HEX`) in nicknames.
- `disguisecore.others`: Permission to manage disguises for other players.
- `disguisecore.realname`: Permission to uncover disguised players.
- `disguisecore.bypass.blacklist`: Permission to bypass name blacklist.

---

## 🎨 Interactive In-Game GUI Dashboard (`/disguisecore` or `/dc`)
* **Strict Non-OP Isolation**: YouTubers and content creators only see their own disguise tools and skin wardrobe; staff oversight panels and system security tabs are completely hidden from non-staff players.
* **Skin Wardrobe Grid**: One-click equipping for famous creators (**ClownPierce**, **Technoblade**, **Dream**, **Camman18**, etc.) with left-click (equip skin) and right-click (equip skin + disguise nickname).
* **System & Security Panel**: Live LuckPerms status, SkinsRestorer auto-restore toggle, AuthMe UUID integrity check, and one-click update checking.

---

## 📄 License & Copyright

**Copyright © 2026 Krishna Mittal. All Rights Reserved.**

This software and its source code are proprietary. Unauthorized copying, reverse engineering, redistribution, or modification of this software, via any medium, is strictly prohibited without the express written permission of the author, **Krishna Mittal** (`krishnamittal0409@gmail.com`).
