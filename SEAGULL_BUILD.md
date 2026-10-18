# Geode 2.209 - Seagull build

This branch is pinned to the last Geode v6 loader commit that still targeted **Geometry Dash 2.209**:

- Loader base commit: `66ea0df7c86b6c5522434b0ca2e23ecd65a742bf`
- GD target: `2.209`
- Comparable GD version: `22090`
- Intended platform: **Windows x64**

The build intentionally lets CMake fetch the current `geode-sdk/bindings` `main` branch, which contains the newer repairs to the dedicated `bindings/2.209` set.

## Why this branch exists

Current Geode v6 has already moved its loader headers to 2.2091. Simply changing its version number back to 2.209 causes header/bindings mismatches. This branch avoids that by pairing the actual 2.209-era loader with the latest 2.209 bindings.

## Build

The easiest reproducible build is the fork branch:

`seagull-2209-exact-build`

Its existing Geode GitHub Actions workflow builds the Windows loader with the same toolchain Geode uses upstream.

For a local source build, Geode requires its normal development prerequisites (Git, CMake 3.25+, C/C++ toolchain, Ninja, and network access for CPM dependencies). A normal configure/build shape is:

```powershell
cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=RelWithDebInfo
cmake --build build --config RelWithDebInfo --parallel
```

This is development code. A successful compile validates the build chain; runtime compatibility still needs testing inside Geometry Dash 2.209.
