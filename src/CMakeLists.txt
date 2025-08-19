# Collect sources
file(GLOB_RECURSE RAYDOCK_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/*.*")

# Build the static library
if(RAYDOCK_SOURCES)
	add_library(raydock STATIC ${RAYDOCK_SOURCES})
endif()

# Expose include directories so examples can find headers
target_include_directories(raydock PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})