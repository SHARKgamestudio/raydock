# Collect sources
file(GLOB_RECURSE RAYDOCK_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/*.*")

# Build the static library
if(RAYDOCK_SOURCES)
	add_library(raydock STATIC ${RAYDOCK_SOURCES})
endif()

# link against raylib (static lib)
target_link_libraries(raydock PUBLIC raylib)

# link against raygui (header only)
include_directories(${raygui_SOURCE_DIR})

# Expose include directories so examples can find headers
target_include_directories(raydock PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})