set(root ../../c-toxcore/testing)

add_library(toxcore_misc_tools
    ${root}/misc_tools.c
)
target_include_directories(toxcore_misc_tools
    PUBLIC
        ${root}
)
target_link_libraries(toxcore_misc_tools
    PUBLIC
        toxcore
)
