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
| clang-format / clang-tidy | LLVM 20 documented, 23.1 on the maintainer machine | `.clang-format` |
| StyLua, luacheck, busted | not pinned yet | `.agents/skills/lua-*` |

## Dependencies (`extern/`)

`Declared` is `configs/submodules.toml`; `Pinned` is the commit the submodule
actually points to (`git submodule status`). They disagree: aligning them is
open work.

| Dependency | Declared | Pinned |
| --- | --- | --- |
| doctest | `v2.4.12` | `v2.5.0` (`d44d4f6`, 121 commits past `v2.4.12`) |
| glm | `1.0.3` | `0.9.5.3-2974` (`6f14f47`, diverged from `1.0.3`) |
| libjpeg-turbo | `3.1.3` | `2.1.4-718` (`03c9a9d`, 283 commits past `3.1.3`) |
| yasm | branch `xavierbeheydt/v1.3.0-cmake-modernization` | `v1.3.0-109` (`09d1bc9`, diverged from that branch) |

## Project

| | Version | Source |
| --- | --- | --- |
| AetherEngine | 0.1.0 | `CMakeLists.txt` (`project(... VERSION ...)`) |
