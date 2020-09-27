project(toxencryptsave)

set(root ../../c-toxcore)

add_library(${PROJECT_NAME}
    ${root}/toxencryptsave/toxencryptsave.c
)

target_link_libraries(${PROJECT_NAME}
    PRIVATE
        sodium
        toxcore
)

if(TOXCORE_ENABLE_TESTING)
    add_subdirectory(test)
endif()
