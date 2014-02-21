project(gameclient.pcsx-rearmed)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(xbmc REQUIRED)

include(ExternalProject)

externalproject_add(pcsx-rearmed
                    GIT_REPOSITORY https://github.com/libretro/pcsx_rearmed
                    GIT_TAG c6c27cc
                    PREFIX pcsx-rearmed
                    CONFIGURE_COMMAND ""
                    INSTALL_COMMAND ""
                    BUILD_COMMAND make -f Makefile.libretro
                    BUILD_IN_SOURCE 1)

set(PCSX-REARMED_CUSTOM_BINARY ${PROJECT_BINARY_DIR}/pcsx-rearmed/src/pcsx-rearmed/pcsx_rearmed_libretro${CMAKE_SHARED_LIBRARY_SUFFIX}
                               pcsx_rearmed_libretro${CMAKE_SHARED_LIBRARY_SUFFIX} pcsx-rearmed)

build_addon(gameclient.pcsx-rearmed PCSX-REARMED DEPLIBS)
add_dependencies(gameclient.pcsx-rearmed pcsx-rearmed)
