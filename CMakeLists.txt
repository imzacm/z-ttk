cmake_minimum_required(VERSION 3.26)
project(
  z-ttk
  VERSION 0.1.0
  DESCRIPTION "Zac's Tiny Toy Kernel"
  LANGUAGES C)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")

if(CMAKE_PROJECT_NAME STREQUAL PROJECT_NAME)
  # Optionally set things like CMAKE_CXX_STANDARD,
  # CMAKE_POSITION_INDEPENDENT_CODE here
  set(CMAKE_C_STANDARD 99)

  # Let's nicely support folders in IDEs
  set_property(GLOBAL PROPERTY USE_FOLDERS ON)

  if(CMAKE_C_COMPILER_ID STREQUAL "OpenWatcom")
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -za99")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -ze")

    if(CMAKE_SYSTEM_PROCESSOR STREQUAL "I86")
      set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -bt=dos -lr")
    endif()
  endif()
endif()

add_library(kernel_include INTERFACE)
target_include_directories(kernel_include INTERFACE include)

# add_subdirectory(mem)
# add_subdirectory(fs)
# add_subdirectory(drivers)
add_subdirectory(kernel)
add_subdirectory(arch)
