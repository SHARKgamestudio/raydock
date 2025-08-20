cmake_minimum_required(VERSION 3.25)

# Setup the project and settings
project(raydock LANGUAGES C VERSION 1.1.0)

# Set the C standard
set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

# --- Options ---
option(RAYDOCK_BUILD_EXAMPLES "Build examples" ON)
option(RAYDOCK_FETCH_DEPS "Automatically fetch dependencies if not found" ON)

# --- Dependencies ---
include(FetchContent)

# Raylib
if (RAYDOCK_FETCH_DEPS)
    include(FetchContent)
    FetchContent_Declare(
        raylib
        GIT_REPOSITORY https://github.com/raysan5/raylib.git
        GIT_TAG 5.5
    )
    FetchContent_MakeAvailable(raylib)
else()
    find_package(raylib REQUIRED)
endif()

# Raygui
if (RAYDOCK_FETCH_DEPS)
    FetchContent_Declare(
        raygui
        GIT_REPOSITORY https://github.com/raysan5/raygui.git
        GIT_TAG master
    )
    FetchContent_MakeAvailable(raygui)
else()
    find_path(raygui_INCLUDE_DIRS "raygui.h")
endif()

# --- Library ---
add_subdirectory(src)

# --- Examples ---
if (RAYDOCK_BUILD_EXAMPLES AND PROJECT_IS_TOP_LEVEL)
    add_subdirectory(examples)
endif()