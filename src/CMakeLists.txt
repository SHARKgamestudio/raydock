# Collect sources
file(GLOB_RECURSE RAYDOCK_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/*.*")

# Build the static library
if(RAYDOCK_SOURCES)
	add_library(${PROJECT_NAME} ${RAYDOCK_SOURCES})
endif()

if(BUILD_SHARED_LIBS)
	# Add a macro defenition to indicate we are building a shared lib
	target_compile_defenitions(${PROJECT_NAME} PRIVATE -DBUILD_LIBTYPE_SHARED)
endif()

# link against raygui (header only)
include_directories(${raygui_SOURCE_DIR})

# Expose include directories so examples can find headers
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
