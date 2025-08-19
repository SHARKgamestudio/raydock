cmake_minimum_required(VERSION 3.25)

project(raydock LANGUAGES C VERSION 1.1.0)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

# Add the library
add_subdirectory(src)

# Add all examples
add_subdirectory(examples)