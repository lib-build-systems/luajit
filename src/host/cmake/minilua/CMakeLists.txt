# Based off of https://github.com/WohlSoft/LuaJIT
cmake_minimum_required(VERSION 3.0)

project(minilua)

find_library(LIBM_LIBRARIES NAMES m)

# Prevent Windows from creating a Debug or Release folder where the executable is installed.
# The CMakeLists.txt wouldn't be able to find the minilua.exe file.
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_CURRENT_BINARY_DIR})
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_CURRENT_BINARY_DIR})

add_executable(minilua ../../minilua.c)
if (LIBM_LIBRARIES)
  target_link_libraries(minilua ${LIBM_LIBRARIES})
endif()
