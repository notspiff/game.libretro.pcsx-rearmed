project(game.libretro.pcsx-rearmed)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(Kodi REQUIRED)
find_package(libretro-pcsx-rearmed REQUIRED)

set(DEPLIBS pcsx-rearmed)
set(PCSX_REARMED_CUSTOM_BINARY ${PCSX_REARMED_LIB}
                               ${PROJECT_NAME}${CMAKE_SHARED_LIBRARY_SUFFIX} pcsx-rearmed)

build_addon(${PROJECT_NAME} PCSX_REARMED DEPLIBS)

