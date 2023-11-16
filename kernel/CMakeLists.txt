add_library(kernel_obj OBJECT
    main.c)

target_link_libraries(kernel_obj PUBLIC kernel_include)
