# Collect sources
file(GLOB_RECURSE RAYDOCK_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/*.c")

# Build the static library
if(RAYDOCK_SOURCES)
	add_library(${PROJECT_NAME} STATIC ${RAYDOCK_SOURCES})
else()
	message(FATAL_ERROR "No source files found for raydock library.")
endif()

# Link against raylib (static lib)
target_link_libraries(${PROJECT_NAME} PUBLIC raylib)

# Link against raygui (header only)
include_directories(${raygui_SOURCE_DIR})

# Expose include directories so examples can find headers
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})