include(TargetArch)
target_architecture(TARGET_ARCH)

if(TARGET_ARCH MATCHES "^(arm|armv5|armv6|armv7)$")
    set(ARCH_ARM ON)
elseif(TARGET_ARCH STREQUAL "i86")
    add_subdirectory(x86-16)
elseif(TARGET_ARCH STREQUAL "i386")
    add_subdirectory(x86-32)
else()
    message(FATAL_ERROR "Unsupported target architecture: ${TARGET_ARCH}")
endif()
