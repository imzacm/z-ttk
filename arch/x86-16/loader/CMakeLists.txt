add_executable(loader
    main.c)

add_custom_command(TARGET loader
    COMMAND ${CMAKE_COMMAND} -E copy
    $<TARGET_FILE:loader>
    ${CMAKE_CURRENT_BINARY_DIR}/loader.com
    COMMENT "Copying loader.exe to ${CMAKE_CURRENT_BINARY_DIR}/loader.com")

if(CMAKE_C_COMPILER_ID STREQUAL "OpenWatcom")
    string(REPLACE "system dos" "system com" new_link_flags ${CMAKE_EXE_LINKER_FLAGS})
    set(CMAKE_EXE_LINKER_FLAGS "${new_link_flags}")
endif()
