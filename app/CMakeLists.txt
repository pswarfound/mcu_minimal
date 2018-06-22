INCLUDE_DIRECTORIES(./include)

aux_source_directory(./ _SRC)
LINK_DIRECTORIES(${PROJECT_BINARY_DIR}/lib)
add_executable(app ${_SRC})
TARGET_LINK_LIBRARIES(app
    -Wl,--whole-archive
    hal
    -Wl,--no-whole-archive
)
add_dependencies(app hal)
