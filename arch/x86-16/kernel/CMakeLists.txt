add_executable(kernel
    main.c)

target_link_libraries(kernel PRIVATE kernel_obj)

add_custom_command(TARGET kernel
    COMMAND ${CMAKE_COMMAND} -E copy
    $<TARGET_FILE:kernel>
    ${CMAKE_CURRENT_BINARY_DIR}/kernel.com
    COMMENT "Copying kernel.exe to ${CMAKE_CURRENT_BINARY_DIR}/kernel.com")

if(CMAKE_C_COMPILER_ID STREQUAL "OpenWatcom")
    string(REPLACE "system dos" "system com" new_link_flags ${CMAKE_EXE_LINKER_FLAGS})
    set(CMAKE_EXE_LINKER_FLAGS "${new_link_flags}")
endif()
