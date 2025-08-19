cmake_minimum_required(VERSION 3.25)

# Setup the project and settings
project(raydock LANGUAGES C VERSION 1.1.0)

# Set the C standard
set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

# --- Fetch raylib ---
include(FetchContent)
FetchContent_Declare(
    raylib
    GIT_REPOSITORY https://github.com/raysan5/raylib.git
    GIT_TAG 5.5
)
FetchContent_MakeAvailable(raylib)

# --- Fetch raygui ---
FetchContent_Declare(
    raygui
    GIT_REPOSITORY https://github.com/raysan5/raygui.git
    GIT_TAG master
)
FetchContent_MakeAvailable(raygui)

# Add the library
add_subdirectory(src)

# Add all examples
add_subdirectory(examples)