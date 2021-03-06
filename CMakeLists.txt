cmake_minimum_required(VERSION 2.8)
project(minimal)

set(CMAKE_SYSTEM_NAME Generic)
set(CMAKE_SYSTEM_PROCESSOR arm)
set(CMAKE_CROSSCOMPILING TRUE)

set(CMAKE_C_COMPILER arm-none-eabi-gcc)
set(CMAKE_CXX_COMPILER arm-none-eabi-c++)
set(CMAKE_STRIP arm-none-eabi-strip)
set(CMAKE_ASM_COMPILER arm-none-eabi-as)
set(CMAKE_RANLIB arm-none-eabi-ranlib)
set(CMAKE_AR arm-none-eabi-ar)

set(CMAKE_SHARED_LIBRARY_LINK_C_FLAGS "")
set(CMAKE_SHARED_LIBRARY_LINK_CXX_FLAGS "")
add_definitions(-DDEBUG)
add_definitions(-DHSE_VALUE=25000000)
add_compile_options(-mcpu=cortex-m7 -mthumb -mfloat-abi=softfp -Os -fmessage-length=0 -fsigned-char -ffreestanding -fno-move-loop-invariants -Wall -Wextra  -g3 -Wno-missing-declarations -MMD -MP)

set(CMAKE_EXE_LINKER_FLAGS
"-mcpu=cortex-m7 -mthumb -mfloat-abi=softfp -Og -fmessage-length=0 -fsigned-char -ffreestanding -fno-move-loop-invariants -Wall -Wextra  -g3 -T mem.ld -T libs.ld -T sections_mem.ld -nostartfiles -Xlinker -L${PROJECT_BINARY_DIR}/lib -Wl,-Map,\"dem.map\"  --specs=nosys.specs"
)

add_subdirectory(hal)
add_subdirectory(app)

