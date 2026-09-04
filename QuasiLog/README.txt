═══════════════════════════════════════════════════════════
  QUASILOG v0.9.4 - README
  A Quasimorph mod by Vas7eel
═══════════════════════════════════════════════════════════

OVERVIEW
--------

QuasiLog completely replaces the in-game combat log with a much 
improved one. It show's the to-hit %, # of attacks, enemy 
statuses, etc.  You can resize, reposition, and scale to fit your 
setup. Just press L to toggle it anytime. K cycles through menus. 
All output in the log is fully customizable, and you can be saved 
as styles. It's easy to change your log to suit how you 
want it to look and what data you want to show. QuasiLog also has a 
Taunt system, the player and other units in the game will speak
one-liners inspired by 80s/90s action movies. These are displayed 
with a new floatie system above the units, which will show taunts
but also combat info, dmg of attack, wounds etc. One of my goals 
of this mod was to give your mercs and the enemy more personality, 
and to that end you can rename your mercs! You can also give enemy 
units randomly assigned names as well. All taunts, names etc. are 
all txt files so you can edit them to be what you want.
Everything in my mod is customizable.


LICENSE
-------
MIT License (see LICENSE.txt). Free to use and to include/
redistribute in modpacks — just keep the copyright/credit
notice. Copyright (c) 2026 Vas7eel.


CONTROLS
--------
  L             - Toggle the log window on/off (configurable);
                  force-opens it even when auto-hidden
  K             - Swap panel (LOG <-> PREFS)
  Drag title    - Move the window
  ◢ grip        - Resize from the bottom-right corner
  - / +         - Decrease / increase font size
  40%           - Cycle background opacity
                  (0%, 20%, 40%, 60%, 80%, 100%)
  ✕             - Clear the log
  LOCK          - Lock/unlock auto-scroll to the newest entry
  LOG           - Combat log panel
  PREFS         - Settings (changes save live)


PREFS
-----
  Toggles       - Start visible, Auto-scroll, Debug logging
  Sliders       - Font size, Background opacity, Max scrollback
  Base text color
                - The color of text the game doesn't tint
                  itself ("To Hit", "damage to", "is dead").
                  Defaults to "auto" = the game's own log green;
                  adjust with the R/G/B sliders or press
                  "Match game" to snap back to auto.
  Reset prefs   - Appearance/behavior back to defaults;
                  the window is NOT moved or resized
  Reset window  - Re-center/size the window; prefs untouched


CHANGELOG
---------
 v0.9.4
    - NEW: "Show Uber dmg Details" (PREFS > Behavior) — Display a detailed 
      breakdown of each attack showing where the damage came from:
      "[dmg] 18 = base 12 (1 hit, 10-18 each) + 8 crit = 20 - 2 resist (10%)"
    - NEW: hover that same line for a tooltip that details buffs and nerfs
      that affected the hit — the perk, the fire mode, the ammo etc. 
    - fix: the scroll wheel released LOCK from anywhere on screen, but no longer
    - fix: the damages bill went blank past 999,999 - Now rack up a highscore
 v0.9.3
    - NEW: identical enemies can now be told apart. "Male Worker A" hits,
      "Female Worker B" dies etc. the same name follows that enemy all
      mission, in the log, the floaties, the STATS table and its inspect
      window. A second toggle swaps the gender and letter for a
      personal name instead ("Worker Ripley", "Brigadier Murtaugh"),
      drawn from an editable UnitNames.txt in your mod config folder.
      Names are stable across a save reload, and no two enemies alive
      at once share one. Human enemies only for the moment.
    - NEW: "Show detailed to-hit and their rolls" — the "[NN%]" moves
      onto its own line carrying every shot's roll and the target's
      dodge: "[95%] - rolls 91/45/98/x - dodge 30". A trailing "x"
      marks a shot that scattered wide and never got to roll. Guns
      only.
    - NEW: attack lines can show the firing weapon's remaining ammo,
      "[ammo: 8/10]", (never worked fully until now)
    - change: the "[NN%]" sits on the hit line instead of beside the
      attacker's name, and the line reads shots landed / shots fired,
      so "3/5 hits" covers the whole trigger pull
    - change: damage types show the game's own name instead of the
      raw internal id — "entropy" not "chaos", "radiation" not "beam"
    - fix: to-hit percentages were being handed to the wrong shot. A
      miss creates no log entry anywhere in the game, and neither does
      a shot that arrives after the target is already dead, so every
      one of those silently pushed the queue out of step and a
      high-accuracy weapon would report a wildly low "[NN%]". The
      percentage, the rolls and the dodge now all ride on the shot
      that produced them
    - fix: two separate attacks in the same turn no longer merge into
      one line, so a later shot's kill can't be credited to an
      earlier one. Thrown weapons no longer borrow the last shooter's
      rolls either
    - fix: a spread weapon hitting two enemies no longer prints the
      whole volley's roll list on both lines
    - fix: mission STATS survive continuing a save
    - fix: loading a save from a different slot no longer shows the
      previous campaign's log and stats
    - fix: enemy names no longer leak raw text like
      "monster.giant.name" into grenade, hazard and wound lines
    - change: a player who has never picked a color style now starts
      on the shipped Default.json instead of "(none)"
 v0.9.2
    - fix: missed shots are only reported if you actually have line
      of sight to them
    - fix: ally status changes are only logged if you have line of
      sight to them
 v0.9.1
    - fix: STATS/taunts no longer mix up allies with your operative
      after continuing a save, and status lines (Stunned, Frozen, etc.)
      no longer show for units you can't actually see
 v0.9.0
    - NEW: accurate to-hit % shown right in the log, worked out from the
      game's own combat math instead of an outside tool
    - NEW: gorier, more varied wound and amputation descriptions, so the
      same injury doesn't read the same way every time
    - NEW: save and swap between named color themes for the log — ships
      with four ready-made ones to start from
    - NEW: end-of-mission stats now also track distance moved, doors
      opened, and stuff destroyed, plus a made-up "damages bill"
    - NEW: status effects (stunned, panicked, suppressed, etc.) now get
      their own log line instead of only showing as an icon
    - NEW: shots that miss out of sight now get logged too, instead of
      disappearing without a trace
    - NEW: every bit of log text can now have its own color
    - fix: small windows no longer swallow the resize-grip click
    - fix: some damage log lines showed junk text instead of the
      damage type
    - fix: combat log no longer stutters during fast multi-hit attacks
 v0.7.2
    - fix: active tab text on LOG / STATS / PREFS / ADMIN (and STATS
      sub-tabs) is now yellow (matches the game's own tab style)
      instead of green. LOCK button stays green when active
 v0.7.1
    - NEW (ADMIN): "Rise" section with a Y travel multiplier float
      input — scales how far floaties rise over their lifetime
      (1.0 = default, 0.5 = half, 1.75 = farther; live, no rebuild)
 v0.7.0
    - NEW: optional Mod Configuration Menu (MCM) support. If you run
      MCM, QuasiLog appears in its list as an info panel: a short
      "How to use" section (press L to show/hide, K to cycle panels,
      settings live in Prefs) and an ABOUT block (version, author,
      build date, commit). MCM is optional — QuasiLog works fully
      without it; all settings and show/hide stay on the log itself
 v0.6.0
    - fix: floatie scale animation is now smooth. Scaled numbers are
      drawn as textured glyph quads from the font atlas (like the
      icon) instead of GUI.Label, so they no longer jitter as the
      font re-rasterizes each frame
    - NEW (ADMIN): scale curve is now a normalized 0..1 shape with
      Scale min / max float inputs — the real size bounds it maps to
      (so you can't accidentally shrink to nothing), with numeric
      axis labels on both curves
    - NEW (ADMIN): 4 control points per curve (ease in and out)
    - NEW (ADMIN): "Loop preview" — a big looping sample near the top
      of the screen to watch the fade + scale curves live while editing
 v0.5.0
    - NEW: ADMIN pane (dev test-harness) — set "EnableAdminPane": true
      in QuasiLog_prefs.json to add a 4th panel (K to reach it) with
      live, draggable curve controls for floatie FADE (alpha) and
      SCALE (size pop/grow), a per-type target mask for each effect
      ([Dmg][Crit][Heal][Wound][Cond][Taunt]), test-spawn buttons,
      and a "Copy settings to clipboard" button
    - change: STATS now shows the operative's in-game name (e.g.
      "Francis Reid-Daly") instead of the clone id (a6-i280)
    - change: dropped "SQUAD" wording — the aggregate is now TOTALS
      and the roster is titled by the operative's name
 v0.4.0
    - NEW: QuasiLog now owns the combat floaties. It suppresses the
      game's native flying text at its single choke point and
      re-renders the same damage / crit ("N!") / heal ("+N") numbers
      and wound icons itself — so they honor the duration slider,
      stack cleanly, and never pop off early from the game's fixed
      hint pool. Same-creature hits still merge into one number
      (merge window is adjustable)
    - NEW: PREFS > Floaties — "Take over native flying text" and
      "Show damage numbers" toggles, a Damage color row ("auto" =
      the game's own damage color), and a Merge-window slider
    - NEW: STATS panel (K/tab) — CombatLog-style post-mission stats
      with per-squad-member tabs (offense / effects dealt / defense),
      squad + enemy rankings, and awards
    - change: the duration slider now drives all QuasiLog floaties
      (including the taken-over damage numbers), 1.5s when left at 0
 v0.3.0
    - NEW: floaties for specific injuries (Fracture, Laceration,
      Contusion, Mild burn, Amputated <part> ...) and conditions
      (Stunned, Frozen, Shocked, Overheat, Sick) above the affected
      unit, each toggleable with its own color
    - NEW: Floatie duration slider — also overrides the game's native
      flying combat text (damage/crit/wound/heal) linger time; plus a
      separate floatie font size
    - NEW: CombatLog-style color picker (color swatch + hex field +
      expandable R/G/B) replacing the plain RGB sliders
    - NEW: K swaps between the LOG and PREFS panels
    - NEW: general auto-hide — the log hides whenever a game window is
      open (inventory, enemy info, implants, mission status, ...), with
      a keep-visible exception list (HUD + map) you can edit in
      QuasiLog_prefs.json; L still force-opens it anywhere
    - NEW: version is shown in the window title bar
    - change: background opacity can now go fully transparent (0%),
      steps 0/20/40/60/80/100
    - change: PREFS reorganized into sections with ON/OFF toggles and
      hover tooltips; LOCK and opacity moved out of PREFS (the window
      bar owns them)
    - change: config files renamed to QuasiLog_prefs.json (prefs) and
      QuasiLog_layout.json (window position/size)
    - fix: LOCK auto-scroll now follows the newest line reliably; wheel
      up releases it, scrolling back to the bottom re-engages
    - fix: window resize no longer loses the grip on fast drags
    - fix: bottom-bar "T" centered; LOCK/LOG/PREFS moved to the right;
      button labels no longer clip
    - fix: L shows the window anywhere, even with an empty log
    - fix: stacked floaties on one unit now separate onto their own
      lines instead of overprinting
 v0.2.0
    - NEW: in-window PREFS pane — font size, background opacity
      and max-scrollback sliders, plus Start-visible, Auto-scroll
      and Debug-logging toggles; every change saves live
    - NEW: base text color matches the game's own combat-log
      green by default ("auto"), with R/G/B override and a
      "Match game" button to snap back
    - NEW: bottom bar — font - / +, opacity cycle, clear (✕),
      LOCK (auto-scroll), and LOG / PREFS tabs
    - NEW: press L to toggle the window (configurable key)
    - NEW: mouse over the window no longer falls through to the
      game — no click-to-move/attack, no camera pan, and the
      scroll wheel scrolls the log instead of zooming the map
    - NEW: the log auto-hides while an inventory, health or
      implants screen is open, and returns when you close it
    - NEW: prefs (config.json) and window layout (window.json)
      are separate files, so "Reset prefs" no longer moves the
      window; a separate "Reset window" button handles layout
    - NEW: continuing a mid-mission save restores the log
      history from the game's own combat log (the game autosaves
      almost every turn), so the window isn't blank on Continue
    - fix: bottom-bar button labels no longer clip at the edge
 v0.1.0
    - initial release: a movable, resizable, transparent,
      scrollable combat-log window that mirrors the game's
      combat log with its native coloring, and keeps far more
      scrollback than the small native window


INSTALLATION
------------
  Steam Workshop (recommended once published):
    Subscribe and enable in the in-game mod list.

  Local (for testing / manual install):
    Copy the QuasiLog folder (modmanifest.json + QuasiLog.dll)
    to:
      %USERPROFILE%\AppData\LocalLow\Magnum Scriptum Ltd\
        Quasimorph\LocalUserPresets\QuasiLog\
    Then restart the game. (Local mods load at startup; they
    are not listed in the in-game Workshop mod menu, but the
    Player.log will show "Mod Vas7eel_QuasiLog loaded".)


COMPATIBILITY
-------------
  Quasimorph:   Unity 2022.3 build (0.9.x+)
  Harmony:      bundled with the game (0Harmony.dll)
  More Combat Info: compatible — its extra lines appear in
                    the QuasiLog window too


CONFIG FILES
------------
Auto-generated under:
  %USERPROFILE%\AppData\LocalLow\Magnum Scriptum Ltd\
    Quasimorph_ModConfigs\QuasiLog\

  config.json   - prefs (font, opacity, colors, toggles,
                  toggle key, max scrollback). Delete or use
                  "Reset prefs" to revert to defaults.
  window.json   - window position and size. Delete or use
                  "Reset window" to re-center.


LINKS & CONTACT
---------------
GitHub:   https://github.com/vas7eel/QuasiLog
Discord:  vas7eel
