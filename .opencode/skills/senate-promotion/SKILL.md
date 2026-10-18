---
name: Senate Promotion
description: Use when working with The Senate (WoW guild) ranks or promotions on Discord. Covers the class ladder (Imperator, Consul, Senator, Legionnaire/Civis, Plebeian), the formal Plebeian to Civis/Legionnaire vote, the informal promotion to Senator, and Consul appointments. Includes guild, role, and channel IDs plus the Discord MCP workflow.
---

# Senate Promotion

How ranks and promotions work in **The Senate**, a Roman-themed Horde guild
(World of Warcraft, now building for *WoW Forever*). The absolute authority is
**Ediction** (Discord user id `207270647313727488`), the **Imperator**.

## The ladder

Highest to lowest. Discord's raw role *position* does **not** match this order.

| Rank | Role ID | Meaning |
| --- | --- | --- |
| **Imperator** (Guild Master) | `1481958960234758204` | Ediction. What they say goes. |
| **Consul** (Officer) | `1481960522319659170` | The Consulate — Imperator's right hand. |
| **Senator** (Veteran) | `1489937394118557758` | The voting body. They nominate and vouch. |
| **Legionnaire** (Raider) | `1481959087133429760` | Reliable warrior. **Raid mettle proven.** |
| **Civis** (Member) | `1552667150974586900` | Good person to have around. **Raid mettle not yet proven.** |
| **Plebeian** (Trial) | `1482148705585856706` | New person. |

`Legionnaire` and `Civis` **hold similar standing** — the split recognises
*how* someone contributes, not how much:

> **Civis** = engaged socially, made friends, integrated well. They may not have
> proven themselves in a raid.
> **Legionnaire** = the same, but with proven raid mettle.
> Since the move to *Forever*, the split also distinguishes TBC veterans (Legio)
> from new joiners.

`Captain (Raid Leader)` (`1512058331676672061`) is a **functional** role, not a
rung on this ladder. Treat raid-function roles (Captain, Healer, etc.)
separately from the class ladder.

## Promotion paths

### 1. Plebeian → Civis / Legionnaire — formal (governed by ❗laws❗)
Channel: `❗laws❗` (`1489772511661916171`, single pinned post by Ediction).
Canon law: <https://discord.com/channels/1480600541095530496/1489772511661916171>

1. **Settle in.** Hang around a few weeks — run dungeons, join a battleground,
   sit in Discord. Let people actually meet them.
2. **Nominatio.** After the first few weeks, *any Senator* who has spent real
   time with them may nominate them. A nomination puts the Senator's own
   reputation on the line.
3. **Suffragium.** The nomination goes to the **full Senate** for a vote.
   - 🗣️ **AYE** — you believe in them.
   - 🗣️ **ABSTAIN** — not sure / haven't seen enough.
   - The vote stays open until **enough AYEs for a simple majority**. No
     deadline — when it's there, it's there, and the Plebeian is promoted.

### 2. → Senator — informal (no law; by Senate consensus, ratified by the Imperator)
Channels: `🔒senate-promotion🔒` (`1490001526930935950`) and
`👑senate-discussion👑` (`1490001600918585414`). This is the informal lane.

The shape of it, as it actually happens:

- **The Imperator opens it** — e.g. *"John Bowie up for promotion. He takes the
  jokes like a champ and dishes them right back out. @Senator"*
- **Or a Senator raises a name** — e.g. *"it's been a long time coming for
  Gladzug to join us as a Senator… if you abstain, now is the time"* or
  *"Have we promoted Keanen to senator yet? … I suggest we promote him."*
- **Senators reply in-channel** — "Aye", "Aye, top man", "Aye to both".
  Abstaining is fine but must be a **conscious** abstention.
- **The Imperator closes it** — *"Passes. Thanks all."* They can also shortcut:
  *"Aye enough to vote bypass. Great addition."*

### 3. → Consul — appointed by the Imperator
Not voted on. Ediction appoints Consuls directly:

> "I've had a few DMs about Consul roles. Slide into my DMs if you think you
> have something to add. I'm looking for volunteers, not putting anything on
> anyone!"

Consuls serve "in the Office of The Imperator". The Consulate (appointed
2026-10-11): **Dany**, **Valarian**, **Bazrek**, plus **Disto** as *Honorary
Consul*. **Xulrogg** "The Mediator" served in the hour of need and his service
was ended. Honorary/ex-service titles do not carry the office's expectations.

### 4. → Imperator
Held by **Ediction**. He ascended after the previous GM, **Dany**
(`317573586619727883`), stepped down on 2026-09-14. Not a promotion path —
succession only.

## Governance context

- Senators hold real power: per Dany's resignation, *"the senators in the guild
  have the ability to vote on guild decisions."*
- Only the Imperator and Consuls raiding-lead broadly; raid leading is being
  turned into a **team** with an appointed loot council (see
  `👑senate-discussion👑`).

## Guild reference

| Thing | Value |
| --- | --- |
| Guild | The Senate (`1480600541095530496`) |
| Imperator (human) | Ediction (`207270647313727488`) |
| MCP bot | Ediction Bot (`1561463406047924346`) |
| ❗laws❗ | `1489772511661916171` |
| 📣announcement📣 | `1481950662366466080` |
| 🔒senate-promotion🔒 | `1490001526930935950` |
| 👑senate-discussion👑 | `1490001600918585414` |
| 👑Curia (Senate House)👑 (voice) | `1489972545951367259` |
| 🗡️roster🗡️ | `1490067742718562374` |
| 🎯deserters🎯 | `1536355109661966387` |

## Working the promotion with the Discord MCP

The Discord server is available as MCP tools named `discord` (call as
`tools.discord.<tool>` in Code Mode). Relevant tools:

- `read_messages` — read history (pagination via `before` / `after` / `around`,
  max 100 per call). Use this to **tally AYEs/ABSTAINs** in
  `senate-promotion`.
- `send_message` — post to a channel; the current standard is to ping the
  `@Senator` role (`<@&1489937394118557758>`) when opening or chasing a vote.
- `list_roles`, `get_role_info` — inspect ranks.
- `list_members`, `get_member` — find the candidate and check their roles.

### Typical flow when asked to run a promotion
1. Confirm the target rank and the candidate (resolve via `list_members` /
   `get_member`).
2. **Pleb → Civis/Legio:** confirm a Senator has made a **Nominatio**, then post
   the motion to the Senate and track the vote to a **simple majority**.
   **→ Senator:** post the motion yourself only if instructed by Ediction, or
   relay a Senator's proposal; collect AYEs.
3. Never invent a result. Report the tally and let the Imperator ratify
   ("Passes").

## Operational notes

- **No role-assignment tool.** The Discord MCP exposes no add/remove-role
  function. Applying a rank after a vote must be done manually in Discord (or
  via a bot that manages roles). Do not claim a rank was applied unless you did
  it some other way.
- **Channel discovery quirk.** `list_channels` returns only *parentless*
  channels (i.e. categories). To enumerate real channels, query the Discord API
  directly: `GET /guilds/{guildId}/channels` with `Authorization: Bot <token>`
  (the token is in the `discord` MCP server's `environment`).
- **Voice of the guild.** Announcements come from Ediction and are often framed
  in-RP (e.g. "24 days" letters). Match that register when drafting.
