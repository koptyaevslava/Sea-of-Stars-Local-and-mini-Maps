# Local Map Installer

The installer is a small Windows Forms front end for a separately generated `.lmpkg` ZIP container. It detects Steam libraries, accepts a manually selected Sea of Stars directory, validates BepInEx, verifies package hashes, installs through a staging-directory swap, and removes only `BepInEx/plugins/LocalMap`.

The 0.9.4 package builder selects only active Local Map files. It requires exactly 99 map folders with 512 px tile manifests and rejects file names associated with the separate timing mod.

The payload must contain the 0.9.4 plug-in DLL and both giant landing maps. Map data alone does not fix landing selection in older plug-in versions.

See [Building](../docs/BUILDING.md) for the expected payload layout and commands.
