# openQ4-GameLibs Agent Guide

This file describes project goals, rules, and upstream credits for anyone working on openQ4-GameLibs.

**Project Metadata**
- Name: openQ4-GameLibs
- Author: themuffinator
- Company: DarkMatter Productions
- Version: 0.0.1
- Website: `www.darkmatter-quake.com`
- Repository: `https://github.com/themuffinator/openQ4-GameLibs`
- Companion Engine Repo (local): `E:\Repositories\openQ4`

**Goals**
- Deliver compatibility-focused Quake 4 game libraries for openQ4 integration.
- Preserve behavior required by original Quake 4 SDK expectations and shipped game data.
- Maintain single-player and multiplayer parity where behavior should remain shared.
- Modernize build and maintenance workflows for current systems while avoiding gameplay regressions.
- Keep documentation and attribution current as upstream work is incorporated.

**Repository Rules (Agent-Only)**
- Compatibility with Quake 4 SDK behavior is the primary requirement.
- Treat this repo and `E:\Repositories\openQ4` as one development workspace; cross-repo coordination is expected, not optional.
- Treat public game-library interfaces used by the engine as stability boundaries unless coordinated cross-repo changes are intentional.
- Prefer engine or code fixes over shipping replacement content files when resolving compatibility issues.
- Keep `README.md` end-user focused: no local machine paths, no maintainer-only rules, and no internal-only process notes.
- Keep local references and maintainer procedures in `AGENTS.md`.
- Keep `README.md` and this file aligned when project direction changes.
- Retain both single-player and multiplayer build targets unless an explicit deprecation plan exists.
- Keep credits accurate and append attributions for newly integrated upstream/third-party work.

**Development Procedure (Recommended)**
1. Build game libraries with Meson/Ninja. On Windows use `tools/build/meson_setup.ps1`; on Linux/macOS use `meson setup --wipe builddir . --backend ninja --buildtype release`, then `meson compile -C builddir`.
2. Validate behavior using openQ4 (`E:\Repositories\openQ4`) against original Quake 4 assets.
3. Review runtime logs in the active Quake 4 install.
4. Iterate until compatibility and stability targets are met.

**Multiplayer Testing (Agent-Only)**
- Keep `ui_autoJoin 1` enabled for multiplayer testing so clients enter gameplay automatically. Use an explicit `+set ui_autoJoin 0` only when the test specifically targets the join menu or initial spectator/join flow; do not rely on omission because the setting is archived.

**Cross-Repo Workflow (Agent-Only)**
- openQ4 (`tools/build/meson_setup.ps1`) can trigger this repo's standalone build during openQ4 compile runs when `OPENQ4_BUILD_GAMELIBS=1`.
- openQ4 consumes this repository as the canonical source-input repository for SDK/game-library code and stages the files it needs during the engine build.
- Keep standalone Linux x64 and arm64 SP/MP module builds supported alongside the openQ4 staged engine build.
- Keep native Linux x64 and arm64 build checks here so portability regressions are caught before openQ4 stages these sources.
- Do not maintain or edit an openQ4 `src/game` mirror; apply canonical game-library source edits here first.

**Local References (Agent-Only, Not Included In Repo)**
- openQ4 engine project: `E:\Repositories\openQ4`
- Quake 4 SDK: `E:\_src\\_CODE\Quake4-1.4.2-SDK`
- Upstream engine base (local folder name retained): `E:\_src\\_CODE\Quake4Doom-master`
- Quake 4 BSE (Basic Set of Effects): `E:\_src\\_CODE\Quake4BSE-master`
- Quake 4 engine decompiled (Hex-Rays): `E:\_src\\_CODE\Quake4Decompiled-main`

**Upstream Credits**
- Upstream Quake4SDK (Quake 4 v1.4.2 SDK baseline).
- id Software.
- Raven Software.
- openQ4 contributors.
- Justin Marshall.
- Robert Backebans.
