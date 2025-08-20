# Collect sources
file(GLOB SANDBOX_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/*.c")

# Create the executable
add_executable(sandbox ${SANDBOX_SOURCES})

# Link against raydock
target_link_libraries(sandbox PRIVATE raydock)