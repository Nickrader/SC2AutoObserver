cmake_minimum_required(VERSION 3.10)

project(Observer)

# Specify output directories.
set(EXECUTABLE_OUTPUT_PATH "${PROJECT_BINARY_DIR}/bin")

# Build with c++14 support required by sc2api.
# Build with c++17 support required by ToolsCommon.
set(CMAKE_CXX_STANDARD 17)

# Disable building of examples in the cpp-sc2 submodule.
set(BUILD_API_EXAMPLES OFF CACHE INTERNAL "" FORCE)

# Disable building of tests in the cpp-sc2 submodule.
set(BUILD_API_TESTS OFF CACHE INTERNAL "" FORCE)

include(FetchContent)
message(STATUS "FetchContent: googletest")

FetchContent_Declare(
  googletest
  GIT_REPOSITORY https://github.com/google/googletest.git
  GIT_TAG 9b12f749fa972d08703d8459e9bf3239617491ca
)

# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)

FetchContent_MakeAvailable(googletest)
# Search for Google test suite.
# //find_package(GTest REQUIRED)
#include_directories(${GTEST_INCLUDE_DIRS})

if (MSVC)
    # Setup MSVC parallelized builds.
    add_compile_options(/MP)

    # Use statically linked runtime.
    #set(CMAKE_MSVC_RUNTIME_LIBRARY MultiThreaded$<$<CONFIG:Debug>:Debug>)    
	set(CMAKE_MSVC_RUNTIME_LIBRARY MultiThreaded$<$<CONFIG:Debug>:Debug>)
	set(CMAKE_MSVC_RUNTIME_LIBRARY MultiThreaded$<$<CONFIG:Release>:Release>)
endif ()

add_subdirectory("cpp-sc2")
add_subdirectory("src")
add_subdirectory("test")
