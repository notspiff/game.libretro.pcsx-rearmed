# game.libretro.pcsx-rearmed
[![Build Status](https://travis-ci.org/kodi-game/game.libretro.beetle-gba?branch=master)](https://travis-ci.org/kodi-game/game.libretro.beetle-gba)
[![Build Status](https://ci.appveyor.com/api/projects/status/github/kodi-game/game.libretro.beetle-gba?svg=true)](https://ci.appveyor.com/project/kodi-game/game-libretro-beetle-gba)

PCSX-rearmed game add-on for Kodi

# Building out-of-tree

## Linux

Create and enter a build directory

```shell
mkdir game.libretro.pcsx-rearmed
cd game.libretro.pcsx-rearmed
```

Generate a build environment with config for debugging

```shell
cmake -DADDONS_TO_BUILD=game.libretro.pcsx-rearmed \
      -DCMAKE_BUILD_TYPE=Debug \
      -DCMAKE_INSTALL_PREFIX=$HOME/workspace/xbmc/addons \
      -DPACKAGE_ZIP=1 \
      $HOME/workspace/xbmc/project/cmake/addons
```

The add-on can then be built with `make`.

# Building in-tree

Kodi's build system will fetch the add-on from the GitHub URL and git hash specified in [game.libretro.pcsx-rearmed.txt](https://github.com/garbear/xbmc/blob/retroplayer-15alpha2/project/cmake/addons/addons/game.libretro.pcsx-rearmed/game.libretro.pcsx-rearmed.txt).

## Linux

Configure Kodi using `./configure --prefix=$HOME/kodi`. Then run `make` and `make install`.

Build the add-on

```shell
make -C tools/depends/target/binary-addons PREFIX=$HOME/kodi ADDONS="game.libretro.pcsx-rearmed"
```

The compiled .so can be found at

```
$HOME/kodi/lib/kodi/addons/game.libretro.pcsx-rearmed/game.libretro.pcsx-rearmed.so
```

To rebuild the add-on or compile a different one, clean the build directory

```shell
make -C tools/depends/target/binary-addons clean
```

## Windows

We will use CMake to generate a `kodi-addons.sln` Visual Studio solution and project files. Add-ons can be built individually through their specific project, or all at once by building the solution.

First, download and install [CMake](http://www.cmake.org/download/) and [MinGW](http://www.mingw.org/). Add the MinGW `bin` folder to your path (e.g. `C:\MinGW\bin`).

Run the script from [PR 6658](https://github.com/xbmc/xbmc/pull/6658) to create Visual Studio project files

```
tools\windows\prepare-binary-addons-dev.bat
```

The generated solution can be found at

```
project\cmake\addons\build\kodi-addons.sln
```

No source code is downloaded at the CMake stage; when the project is built, the add-on's source will be downloaded and compiled.

## OSX

Per [README.osx](https://github.com/garbear/xbmc/blob/retroplayer-15alpha2/docs/README.osx), enter the `tools/depends` directory and make the add-on:

```shell
cd tools/depends
make -C target/binary-addons ADDONS="game.libretro.pcsx-rearmed"
```

To rebuild the add-on or compile a different one, clean the build directory

```shell
make -C target/binary-addons clean
```
