project(toxencryptsave)

set(ROOT ${CMAKE_SOURCE_DIR}/c-toxcore)

add_library(${PROJECT_NAME}
    ${ROOT}/toxencryptsave/toxencryptsave.c
)

target_link_libraries(${PROJECT_NAME}
    PRIVATE
        sodium
        toxcore
)

if(TOXCORE_ENABLE_TESTING)
    add_subdirectory(test)
endif()
