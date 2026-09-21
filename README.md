# AnoMech Testing

Testing builds of [Evernow/AnoMech](https://github.com/Evernow/AnoMech)'s `multiplayer-support`
branch. Nothing here is edited by hand — `main` holds only the workflow, and `mirror` is a
read-only copy of the branch as of the last build.

The workflow checks the branch every 15 minutes (and on demand from the Actions tab). When the
branch has moved it builds a Release plugin, renames it to `AnoMechTesting` so it installs
alongside upstream's AnoMech with its own config, and cuts a release tagged `src-<short sha>`
carrying `AnoMechTesting.zip` and `AnoMechTesting.json`.

`Evernow/DalamudPlugins` picks those up on its own 20-minute sync and updates
`pluginmaster.json`, so installing is just the usual custom repo:

```
https://raw.githubusercontent.com/Evernow/DalamudPlugins/main/pluginmaster.json
```

Version numbers are `<major>.<minor>.<build>` from the branch's csproj with the workflow run
number as the revision, so every build is newer than the last and Dalamud offers the update.
