cmake_minimum_required(VERSION 3.25)

# Setup the project and settings
project(raydock LANGUAGES C VERSION 1.1.0)

# Set the C standard
set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

# --- Fetch raylib ---
include(cmake/CPM.cmake)
CPMAddPackage("gh:raysan5/raylib#master")

# --- Fetch raygui ---
CPMAddPackage("gh:raysan5/raygui#master")

# Add the library
add_subdirectory(src)

option(RAYDOCK_BUILD_EXAMPLES "Build examples for raydock" ${PROJECT_IS_TOP_LEVEL})

if(RAYDOCK_BUILD_EXAMPLES)
	# Add all examples
	add_subdirectory(examples)
endif()
