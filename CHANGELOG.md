# Changelog

## 0.9.4

- Added maps for X'tol's Landing and Evermist Island's Landing.
- Fixed map selection at giant landing sites. These areas are streamed into WorldMap, so the mod now follows the game's native custom location reference.
- Clear the landing map when the native location reference resets, and ignore it in ordinary local areas.
- Added a regression test for landing selection, exit, and stale location references.
- Updated the installer source to expect 99 map folders.

## 0.9.3

- Retiled all 97 high-resolution maps into alpha-cropped 512 px tiles.
- Replaced the fixed tile-count cache with a 192 MiB decoded-texture budget.
- Pooled map tile UI objects to avoid hierarchy rebuilds during pan and zoom.
- Added aggregated full-map performance diagnostics to the BepInEx log.
- Kept the full map centered on the player whenever it opens.
- Added discovered campfire and save-point markers using game-style assets.
- Added localized map controls and native per-language font selection.
- Updated the standalone installer with strict payload selection and English UI.
- Limited installer progress callbacks to percentage changes so large install and verify operations do not flood the Windows message queue.
