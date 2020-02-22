function(make_test name)
    add_executable(${name}
        ${ARGN}
    )

    target_link_libraries(${name}
        PRIVATE
            toxcore
    )

    add_test(
        NAME ${name}
        COMMAND ${name}
    )
endfunction()

set(ROOT ${CMAKE_SOURCE_DIR}/c-toxcore)

make_test(crypto_test
    ${ROOT}/auto_tests/crypto_test.c
)

make_test(dht_test
    ${ROOT}/auto_tests/dht_test.c
    ${ROOT}/testing/misc_tools.c
)
