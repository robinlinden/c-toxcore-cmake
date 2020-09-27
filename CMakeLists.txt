cmake_minimum_required(VERSION 3.15)

project(c-toxcore-cmake)

option(TOXCORE_ENABLE_TESTING "" ON)

if(TOXCORE_ENABLE_TESTING)
    enable_testing()
endif()

add_subdirectory(lib)
add_subdirectory(external)
