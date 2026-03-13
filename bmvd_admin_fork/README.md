# Better Mass Vassal Directive — Admin & Celestial Fork

A fork of [Wehrmachtserdbeere's Better Mass Vassal Directive](https://github.com/Wehrmachtserdbeere/better_mass_vassal_directive).

---

## BEFORE YOU USE THIS MOD — ONE REQUIRED EDIT

The obligation filter (`vassal_contract_obligation_level`) needs the internal
key name for the Administrative government's obligation group. This is stored
in the vanilla game files and cannot be confirmed without them.

**How to find it:**

1. Go to your CK3 install folder (Steam default: `SteamApps/common/Crusader Kings III/game/`)
2. Open `common/vassal_contracts/`
3. Find the file that defines the Administrative/Bureaucratic contracts
4. Look for an obligation group containing the levels:
   `balanced`, `military`, `civilian`, `frontier`, `navy`, `imperial`
5. The name of that group (the key before the `=` block) is what you need.
   It will be something like `governor_obligation` or `administrative_obligation`.

6. Open `common/decisions/bmvd_admin_specialization_directives.txt`
7. Do a Find & Replace: replace every instance of `governor_obligation`
   with the correct key you found.

That is the only edit required.

---

## Mod Structure

```
mod_root/
├── descriptor.mod
├── README.md
├── common/
│   └── decisions/
│       └── bmvd_admin_specialization_directives.txt
└── localization/
    └── english/
        └── bmvd_admin_specialization_l_english.yml
```

No vanilla files are overwritten. The mod is purely additive.

---

## How it Works

### Non-Administrative / Non-Celestial Rulers
Six direct decisions appear in your Decisions list — one per directive:
- Train Commanders
- Build Military Buildings
- Build Economical Buildings
- Improve Development
- Convert to Culture
- Convert to Faith

Each applies that directive to all eligible vassals at once. Same as the
original mod behaviour.

### Administrative / Celestial Rulers — Two-Step Flow

**Step 1 — Select a Governor Group**

The following decisions appear (only for groups where you have at least one
vassal of that type):

| Decision | Targets |
|---|---|
| Select Group: Balanced | Vassals with Balanced obligation |
| Select Group: Military | Vassals with Military obligation |
| Select Group: Civilian | Vassals with Civilian obligation |
| Select Group: Frontier | Vassals with Frontier obligation |
| Select Group: Naval | Vassals with Navy obligation |
| Select Group: Imperial | Vassals with Imperial obligation |
| Select Group: All Governors | All vassals regardless of type |

A **Cancel Group Selection** decision also appears while a selection is active,
allowing you to start over.

**Step 2 — Apply a Directive**

After selecting a group, six directive decisions appear — one per directive.
All six are always available regardless of group type; the game lets you
choose freely. A decision will appear greyed out (invalid) if no vassal in
the selected group can currently accept that directive.

On clicking a directive decision, it:
1. Applies the directive to all eligible vassals in the selected group
2. Clears the group selection variable automatically
3. Shows a confirmation tooltip

---

## Compatibility

- No vanilla file overrides — fully compatible with other mods
- Compatible with the original Better Mass Vassal Directive mod (different
  decision keys, no conflicts)
- Administrative decisions require the *Roads to Power* DLC
- Celestial decisions require the *All Under Heaven* DLC
- Tested structure for CK3 1.13+

---

## Credits

Original mod: [Wehrmachtserdbeere](https://github.com/Wehrmachtserdbeere/better_mass_vassal_directive)
