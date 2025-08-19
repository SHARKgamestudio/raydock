file(GLOB SANDBOX_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/*.c")

add_executable(sandbox ${SANDBOX_SOURCES})
target_link_libraries(sandbox PRIVATE raydock)