# CMSIS Build CMakeLists generated on 2024-04-02T12:57:43

cmake_minimum_required(VERSION 3.22)

# Target options

set(TARGET Lab1)
set(CPU Cortex-M4)
set(PRJ_DIR "d:/Embedded Code/TM4C123Valvanoware/Lab1_4C123")
set(OUT_DIR "D:/Embedded Code/TM4C123Valvanoware/Lab1_4C123/out/Lab1/Target")
set(INT_DIR "D:/Embedded Code/TM4C123Valvanoware/Lab1_4C123/tmp/Lab1/Target")
set(FPU NO_FPU)
set(BYTE_ORDER Little-endian)
set(OPTIMIZE none)
set(DEBUG on)
set(AS_FLAGS_GLOBAL "-masm=auto")
set(CC_FLAGS_GLOBAL "-std=c99 -fno-rtti -fsigned-char -fshort-enums -fshort-wchar -ffunction-sections -Wno-packed -Wno-missing-variable-declarations -Wno-missing-prototypes -Wno-missing-noreturn -Wno-sign-conversion -Wno-nonportable-include-path -Wno-reserved-id-macro -Wno-unused-macros -Wno-documentation-unknown-command -Wno-documentation -Wno-license-management -Wno-parentheses-equality")
set(CXX_FLAGS_GLOBAL "-xc++ -std=c++11 -fno-rtti -fsigned-char -fshort-enums -fshort-wchar -ffunction-sections -Wno-packed -Wno-missing-variable-declarations -Wno-missing-prototypes -Wno-missing-noreturn -Wno-sign-conversion -Wno-nonportable-include-path -Wno-reserved-id-macro -Wno-unused-macros -Wno-documentation-unknown-command -Wno-documentation -Wno-license-management -Wno-parentheses-equality")
set(LD_FLAGS_GLOBAL "--map --load_addr_map_info --xref --callgraph --symbols --info sizes --info totals --info unused --info veneers --strict --summary_stderr --info summarysizes")
set(LD_SCRIPT "d:/Embedded Code/TM4C123Valvanoware/Lab1_4C123/RTE/Device/TM4C123GH6PM/ac6_linker_script.sct.src")
set(LD_REGIONS "d:/Embedded Code/TM4C123Valvanoware/Lab1_4C123/RTE/Device/TM4C123GH6PM/regions_TM4C123GH6PM.h")
set(LD_SCRIPT_PP "D:/Embedded Code/TM4C123Valvanoware/Lab1_4C123/tmp/Lab1/Target/ac6_linker_script.sct")

set(DEFINES
  TM4C123GH6PM
  _RTE_
)

set(INC_PATHS
  "d:/Embedded Code/TM4C123Valvanoware/inc"
  "d:/Embedded Code/TM4C123Valvanoware/Lab1_4C123/RTE/_Target"
  "C:/Users/Akmal Narendra Sakti/AppData/Local/Arm/Packs/ARM/CMSIS/5.9.0/CMSIS/Core/Include"
  "C:/Users/Akmal Narendra Sakti/AppData/Local/Arm/Packs/Keil/TM4C_DFP/1.1.0/Device/Include/TM4C123"
)

set(AS_ARM_SRC_FILES
  "d:/Embedded Code/TM4C123Valvanoware/Lab1_4C123/RTE/Device/TM4C123GH6PM/startup_TM4C123.s"
)

set(CC_SRC_FILES
  "d:/Embedded Code/TM4C123Valvanoware/Lab1_4C123/Lab1.c"
  "d:/Embedded Code/TM4C123Valvanoware/Lab1_4C123/RTE/Device/TM4C123GH6PM/system_TM4C123.c"
  "d:/Embedded Code/TM4C123Valvanoware/inc/BSP.c"
  "d:/Embedded Code/TM4C123Valvanoware/inc/Profile.c"
)

set(LIB_FILES
  "d:/Embedded Code/TM4C123Valvanoware/Lab1_4C123/texas.o"
)

# Toolchain config map

set(REGISTERED_TOOLCHAIN_ROOT "c:/Users/Akmal Narendra Sakti/.vcpkg/artifacts/2139c4c6/compilers.arm.armclang/6.21.0/bin")
set(REGISTERED_TOOLCHAIN_VERSION "6.21.0")
set(TOOLCHAIN_VERSION_MIN "6.21.0")
set(TOOLCHAIN_VERSION_MAX "6.21.0")
include ("C:/Users/Akmal Narendra Sakti/.vcpkg/artifacts/2139c4c6/tools.open.cmsis.pack.cmsis.toolbox/2.2.1/etc/AC6.6.18.0.cmake")
include ("C:/Users/Akmal Narendra Sakti/.vcpkg/artifacts/2139c4c6/tools.open.cmsis.pack.cmsis.toolbox/2.2.1/etc/CMSIS-Build-Utils.cmake")

# Setup project

project(${TARGET} LANGUAGES AS_ARM C)

cbuild_get_running_toolchain(TOOLCHAIN_ROOT TOOLCHAIN_VERSION C)

# Global Flags

set(CMAKE_AS_ARM_FLAGS "${AS_ARM_CPU} ${AS_ARM_BYTE_ORDER} ${AS_ARM_DEFINES} ${AS_ARM_OPTIONS_FLAGS} ${AS_ARM_FLAGS} ${AS_FLAGS_GLOBAL}")
cbuild_get_system_includes(CC_SYS_INC_PATHS_LIST CC_SYS_INC_PATHS)
set(CMAKE_C_FLAGS "${CC_CPU} ${CC_BYTE_ORDER} ${CC_DEFINES} ${CC_OPTIONS_FLAGS} ${CC_FLAGS} ${CC_FLAGS_GLOBAL} ${CC_SYS_INC_PATHS}")
set(CMAKE_C_LINK_FLAGS "${LD_CPU} ${_LS}\"${LD_SCRIPT_PP}\" ${LD_FLAGS_GLOBAL} ${LD_OPTIONS_FLAGS} ${LD_FLAGS}")

# Local Flags

foreach(SRC ${AS_ARM_SRC_FILES})
  set_source_files_properties(${SRC} PROPERTIES LANGUAGE AS_ARM)
endforeach()

# Compilation Database

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
add_custom_target(database COMMAND ${CMAKE_COMMAND} -E copy_if_different "${INT_DIR}/compile_commands.json" "${OUT_DIR}")

# Setup Target

add_executable(${TARGET} ${AS_ARM_SRC_FILES} ${CC_SRC_FILES})
set_target_properties(${TARGET} PROPERTIES PREFIX "" SUFFIX ".axf" OUTPUT_NAME "Lab1")
set_target_properties(${TARGET} PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${OUT_DIR} LINK_DEPENDS ${LD_SCRIPT})
target_include_directories(${TARGET} PUBLIC ${INC_PATHS})
target_link_libraries(${TARGET} ${LIB_FILES})

# Linker script pre-processing

add_custom_command(TARGET ${TARGET} PRE_LINK COMMAND ${CPP} ARGS ${CPP_ARGS_LD_SCRIPT} BYPRODUCTS ${LD_SCRIPT_PP})
