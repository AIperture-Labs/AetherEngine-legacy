# Versions

What the project uses, at a glance. The source of truth is in parentheses:
update this page in the same change as the version it lists.

## Languages

| Language | Version | Source |
| --- | --- | --- |
| C++ | 23 | `cmake/Config.cmake` (`CMAKE_CXX_STANDARD`) |
| CMake | 3.31 – 4.1 | `CMakeLists.txt` (`cmake_minimum_required`) |
| Python | 3.14 | `cmake/Config.cmake` (`AETHER_ENGINE_PYTHON_VERSION`) |
| Lua | 5.4 (planned, game scripting) | `.agents/instructions/style/lua.md` |

## Build and tooling

| Tool | Version | Source |
| --- | --- | --- |
| Ninja | any (preset generator) | `CMakePresets.json` |
| Vulkan | 1.4.335 minimum | `cmake/Dependencies.cmake` |
| uv | 0.9.27 | `cmake/Config.cmake` (`AETHER_ENGINE_UV_VERSION`) |
| clang-format / clang-tidy | LLVM 20 | `.clang-format` |
| StyLua, luacheck, busted | not pinned yet | `.agents/skills/lua-*` |

## Dependencies (`extern/`)

| Dependency | Pin | Source |
| --- | --- | --- |
| doctest | `v2.4.12` | `configs/submodules.toml` |
| glm | `1.0.3` | `configs/submodules.toml` |
| libjpeg-turbo | `3.1.3` | `configs/submodules.toml` |
| yasm | branch `xavierbeheydt/v1.3.0-cmake-modernization` | `configs/submodules.toml` |

## Project

| | Version | Source |
| --- | --- | --- |
| AetherEngine | 0.1.0 | `CMakeLists.txt` (`project(... VERSION ...)`) |
