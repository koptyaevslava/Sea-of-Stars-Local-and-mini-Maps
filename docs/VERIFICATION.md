# Verification — 0.9.4

## Automated checks

- Release build: 0 warnings and 0 errors.
- Managed test suite: 19 tests passed, including native custom location selection, exit, and stale-reference cases.
- Map inventory: 99 maps, including X'tol's Landing and Evermist Island's Landing.
- Full package validation: 99 maps and clean overviews, 27,410 detail tiles, 0 errors.
- Every detail tile's SHA-256, PNG dimensions, RGBA mode, nonempty alpha, atlas coordinates, and projection were validated. Tiles are at most 512 by 512 pixels and all manifests fit the runtime limits.
- The current party position at X'tol's Landing projects onto an opaque terrain pixel in its new map.
- Installer 0.9.4 and its package were built. The installer's own verifier passed all 28,306 payload files (828,919,286 bytes).
- The Nexus manual-install ZIP was built from the same verified payload, with no executable installer or nested archive.

## Landing selection diagnosis

Read-only runtime inspection at X'tol's Landing confirmed that CurrentLevel remains WorldMap while StreamingWorldMapManager.CurrentCustomMapLocation identifies YeetGolem. The landing scene contains the game's SetWorldMapCustomMapLocation component. Its native OnEnable sets that reference and OnDisable resets it to LevelReference.None.

Map selection now uses that native reference for the two supported giant landing sites. Ordinary local levels ignore it. Loading and visibility checks use the same resolved map GUID.

## Performance diagnosis

The previous 2048 by 2048 tiles decoded to as much as 16 MiB each and were uploaded synchronously by Unity during pan and zoom. The 512 by 512 layout caps one decoded upload at 1 MiB. Visible tiles are retained under a 192 MiB memory budget and UI tile objects are pooled.

## Manual checks

In-game verification of the 0.9.4 changes has not been performed. The player should check:

1. Open the minimap and full map at both giant landing sites.
2. Leave each landing and confirm that its map disappears on the world map.
3. Enter an ordinary local area and confirm that its own map appears.
4. Confirm that the full map initially centers on the player and that exploration fog persists.
5. Pan and zoom repeatedly in large locations and watch for frame-time spikes.
6. Confirm campfire/save-point markers, controller controls, and localized map prompts.

The game is not launched by the build or verification scripts.
