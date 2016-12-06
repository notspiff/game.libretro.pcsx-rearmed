cmake_minimum_required(VERSION 3.1)
project(game.libretro.pcsx-rearmed)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

find_package(Kodi REQUIRED)
find_package(libretro-pcsx-rearmed REQUIRED)

set(PCSX-REARMED_CUSTOM_BINARY ${PCSX-REARMED_LIB}
    ${PROJECT_NAME}${CMAKE_SHARED_LIBRARY_SUFFIX})

build_addon(${PROJECT_NAME} PCSX-REARMED "")