# QuasiLog

**A Quasimorph mod by Vas7eel** · v0.9.3

A customizable combat log, floatie message system, and taunt pack framework.

QuasiLog completely replaces the in-game combat log with a much improved one. The data
presented is clear, it shows the to-hit % of your attacks, enemy statuses are logged, and you
can **resize, reposition, and scale** it to fit your setup. All text in the log is fully
customizable and can be saved as styles — four ship with the mod to start from. The window
auto-hides when you open in-game menus, so it should feel natural with the game.

It reads the game's own log, so other log mods (More Combat Info) still work alongside it, and
it shows up in MCM if you use it. All preferences are saved to `.json` files.

## Download

- 📦 **[Download QuasiLog.zip](QuasiLog.zip)** — then see Installation below
- 🎮 Also on the [Steam Workshop](https://steamcommunity.com/sharedfiles/filedetails/?id=3779031378)

## Installation

Steam Workshop: subscribe and enable it in the in-game mod list.

Manual (non-Steam, or for testing):

1. Extract `QuasiLog.zip`.
2. Copy the `QuasiLog` folder to:
   `%USERPROFILE%\AppData\LocalLow\Magnum Scriptum Ltd\Quasimorph\LocalUserPresets\QuasiLog\`
3. Restart the game. Local mods load at startup and are not listed in the in-game Workshop mod
   menu, but `Player.log` will show `Mod Vas7eel_QuasiLog loaded`.

Safe to install or remove at any time.

## Compatibility

| | |
|---|---|
| Quasimorph | 1.0.2 (Unity 2022.3 builds, 0.9.x+) |
| Harmony | bundled with the game (`0Harmony.dll`) |
| More Combat Info | compatible — its lines appear in the QuasiLog window too |
| MCM (Mod Configuration Menu) | optional — adds an info/about panel |

## Controls

| Key / Button | Action |
|---|---|
| `L` | Toggle the log window on/off (configurable); force-opens it even when auto-hidden |
| `K` | Cycle panels (LOG / STATS / PREFS) |
| Drag title | Move the window |
| ◢ grip | Resize from the bottom-right corner |
| `-` / `+` | Decrease / increase font size |
| `40%` | Cycle background opacity (0–100%) |
| `✕` | Clear the log |
| `LOCK` | Lock/unlock auto-scroll to the newest entry |

## Taunt packs

Give every agent and enemy a voice. When someone scores a kill, takes a big hit, gets a limb
amputated, or barely survives, they fire off a one-liner. How often they fire, what color they
are, etc. are all customizable. Built-in packs include 80s/90s action hero one-liners and an
Arnold voice pack — or anything you want, make your own.

Packs are just `.txt` files. Copy one of the built-ins as a template, rename it to something
sensible (e.g. `scarface_taunt_pack.txt`), edit the lines under each category header, drop it in
the Taunts folder, reload taunts in-game, and pick it in **QuasiLog → Prefs → Taunts**.

They live in:

```
%USERPROFILE%\AppData\LocalLow\Magnum Scriptum Ltd\Quasimorph_ModConfigs\QuasiLog\Taunts\
```

Drop the `\Taunts\` off the end for the config folder — prefs, styles and `UnitNames.txt` live
there. Delete a file to get the defaults back.

The format:

```
# QuasiLog taunt pack — Arnold Schwarzenegger edition.
# One taunt per line. Blank lines and # comments ignored.
# tokens: {me} {target} {damage} {wound}
#   laststand  - attacker, killing blow, attacker's HP <= near-death threshold
#   kill       - attacker, killing blow (any HP)
#   amputation - attacker, hit caused amputation
#   bighit     - attacker, hit landed, damage >= big-hit threshold, victim survives
#   missedattack - attacker, attack missed
#   ondeath    - victim, this hit killed them
#   missedme   - victim, attack against them missed
#   tookbighit - victim, survived, damage >= big-hit threshold
#   neardeath  - victim, survived, own HP <= near-death threshold

[laststand]
I eat Green Berets for breakfast. And right now, I'm very hungry!
You're a choir boy compared to me!
Of course, I'm a terminator.
```

## Floaties

A floatie message system that overlays more information above the player and units. Damage,
crits, heals, wounds and conditions (Stunned, Frozen, Overheat...) each get their own toggle and
color, with sliders for how long they linger, their font size, and how far they rise. This is
also the backbone of the taunt system.

## Mission stats

A live stats panel shows current mission info at a glance for you and your VIP allies — kills,
damage, injuries caused and suffered, plus fun ones like distance moved, doors opened, and how
much of the environment you blew up (and what the damages would cost).

## Names

Give your agents custom names and monikers in the Agent menu; those names appear in the combat
log and floaties.

Identical enemies get their own name for the mission — "Male Worker A" hits, "Female Worker B"
dies — in the log, the floaties and the stats. Or switch it to personal names ("Worker Ripley"),
from a `UnitNames.txt` you can edit yourself. Human enemies for now.

## Changelog

### v0.9.3

- **NEW:** identical enemies can now be told apart. "Male Worker A" hits, "Female Worker B" dies
  etc. — the same name follows that enemy all mission, in the log, the floaties, the STATS table
  and its inspect window. A second toggle swaps the gender and letter for a personal name instead
  ("Worker Ripley", "Brigadier Murtaugh"), drawn from an editable `UnitNames.txt` in your mod
  config folder. Names are stable across a save reload, and no two enemies alive at once share
  one. Human enemies only for the moment.
- **NEW:** "Show detailed to-hit and their rolls" — the `[NN%]` moves onto its own line carrying
  every shot's roll and the target's dodge: `[95%] - rolls 91/45/98/x - dodge 30`. A trailing `x`
  marks a shot that scattered wide and never got to roll. Guns only.
- **NEW:** attack lines can show the firing weapon's remaining ammo, `[ammo: 8/10]` (never worked
  fully until now).
- change: the `[NN%]` sits on the hit line instead of beside the attacker's name, and the line
  reads shots landed / shots fired, so "3/5 hits" covers the whole trigger pull.
- change: damage types show the game's own name instead of the raw internal id — "entropy" not
  "chaos", "radiation" not "beam".
- fix: to-hit percentages were being handed to the wrong shot. A miss creates no log entry
  anywhere in the game, and neither does a shot that arrives after the target is already dead, so
  every one of those silently pushed the queue out of step and a high-accuracy weapon would report
  a wildly low `[NN%]`. The percentage, the rolls and the dodge now all ride on the shot that
  produced them.
- fix: two separate attacks in the same turn no longer merge into one line, so a later shot's kill
  can't be credited to an earlier one. Thrown weapons no longer borrow the last shooter's rolls
  either.
- fix: a spread weapon hitting two enemies no longer prints the whole volley's roll list on both
  lines.
- fix: mission STATS survive continuing a save.
- fix: loading a save from a different slot no longer shows the previous campaign's log and stats.
- fix: enemy names no longer leak raw text like `monster.giant.name` into grenade, hazard and
  wound lines.
- change: a player who has never picked a color style now starts on the shipped `Default.json`
  instead of "(none)".

Older entries are in [`QuasiLog/README.txt`](QuasiLog/README.txt).

## License

MIT — see [`QuasiLog/LICENSE.txt`](QuasiLog/LICENSE.txt). Free to use and to include or
redistribute in modpacks, just keep the copyright/credit notice. Copyright (c) 2026 Vas7eel.

## Contact

Discord: [QuasiLog channel](https://discord.com/channels/912012292445593630/1538493589406097461) · `vas7eel`
