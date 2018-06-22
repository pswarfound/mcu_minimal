INCLUDE_DIRECTORIES(./)

aux_source_directory(./ _SRC)
aux_source_directory(./newlib _SRC)
aux_source_directory(./diag _SRC)

ADD_library(hal STATIC ${_SRC})
SET(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)


add_custom_command(TARGET hal POST_BUILD
COMMAND ${CMAKE_COMMAND} -E copy ${PROJECT_SOURCE_DIR}/hal/stm32F7/CMSIS/mem.ld ${PROJECT_BINARY_DIR}/lib
COMMAND ${CMAKE_COMMAND} -E copy ${PROJECT_SOURCE_DIR}/hal/stm32F7/CMSIS/sections.ld ${PROJECT_BINARY_DIR}/lib
COMMAND ${CMAKE_COMMAND} -E copy ${PROJECT_SOURCE_DIR}/hal/stm32F7/CMSIS/sections_mem.ld ${PROJECT_BINARY_DIR}/lib
COMMAND ${CMAKE_COMMAND} -E copy ${PROJECT_SOURCE_DIR}/hal/stm32F7/CMSIS/libs.ld ${PROJECT_BINARY_DIR}/lib
)
