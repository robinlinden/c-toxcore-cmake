set(ROOT ${CMAKE_SOURCE_DIR}/c-toxcore)

add_executable(crypto_test
    ${ROOT}/auto_tests/crypto_test.c
)
target_link_libraries(crypto_test
    PRIVATE
        toxcore
)
add_test(
    NAME crypto_test
    COMMAND crypto_test
)

add_executable(dht_test
    ${ROOT}/auto_tests/dht_test.c
    ${ROOT}/testing/misc_tools.c
)
target_link_libraries(dht_test
    PRIVATE
        toxcore
)
add_test(
    NAME dht_test
    COMMAND dht_test
)
