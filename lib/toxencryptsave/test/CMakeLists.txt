set(root ../../../c-toxcore/auto_tests)

function(make_test name)
    add_executable(${name}
        ${root}/${name}
    )

    target_link_libraries(${name}
        PRIVATE
            toxcore
            toxcore_misc_tools
            toxencryptsave
    )

    add_test(
        NAME ${name}
        COMMAND ${name}
    )
endfunction()

make_test(encryptsave_test)

# TODO(robinlinden):
# make_test(file_saving_test)
# fails with:
# written written_value = 1068 of 1068
# Read read_value = 172 of 1074
