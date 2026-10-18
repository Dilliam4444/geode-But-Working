# Seagull Geode 2.209 build

This branch is based on Geode's current `v6` development branch and is retargeted to **Geometry Dash 2.209**.

## What changed
- `GEODE_GD_VERSION` = `2.209`
- `GEODE_COMP_GD_VERSION` = `22090`
- Uses the current `geode-sdk/bindings` main branch, which contains a dedicated `bindings/2.209` set.
- Intended target: **Windows x64 / Geometry Dash 2.209**.

## Easiest way to build
The fork also contains the branch `seagull-v6-2209-build`.
GitHub Actions on that branch runs Geode's own Windows build workflow, so it is the closest thing to a reproducible build without manually setting up Geode's cross-compilation toolchain.

## Local source build
This is normal Geode source, not a pre-generated IDE project. It requires the same prerequisites as Geode itself: Git, CMake 3.25+, a supported C/C++ toolchain, Ninja, and network access for CPM dependencies. The repository's own CMake files fetch the current bindings and other dependencies during configure.

A typical configure/build shape is:

```powershell
cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=RelWithDebInfo
cmake --build build --config RelWithDebInfo --parallel
```

Exact compiler/toolchain setup matters. If local Windows configuration is annoying, use the fork's GitHub Actions Windows build instead.

## Important
This is development Geode code. A successful compile proves the source/build chain is valid; it does **not** guarantee every mod is compatible with GD 2.209.
