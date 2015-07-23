if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE "RelWithDebInfo" CACHE STRING
      "Choose the type of build, options are: None Debug Release RelWithDebInfo Debug Debugfull Profile MinSizeRel."
      FORCE)
endif()

project(bfs2pack)

set(PROGNAME bfs2pack)

cmake_minimum_required(VERSION 2.6.4)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

include(CheckCCompilerFlag)
include(CheckCXXCompilerFlag)
include(CheckCXXSourceCompiles)

option(WITH_TESTS "Enable building of tests" OFF) # Disabled, I don't know what we're testing...
option(WITH_MMGR  "Enable Memory Manager (mmgr)" OFF)

find_package(ZLIB REQUIRED)

add_subdirectory(src)
if(WITH_TESTS)
  add_subdirectory(test)
endif(WITH_TESTS)

if (WITH_MMGR)
  add_gcc_compiler_flags("-D_MMGR")
endif()

if(PRINT_SUMMARY)
  feature_summary(WHAT ALL)
endif()
