cmake_minimum_required(VERSION 3.15)

project(toxcore)

enable_testing()

add_subdirectory(external)

add_library(toxcore
    c-toxcore/toxcore/crypto_core.c
    c-toxcore/toxcore/crypto_core_mem.c
    c-toxcore/toxcore/DHT.c
    c-toxcore/toxcore/friend_connection.c
    c-toxcore/toxcore/friend_requests.c
    c-toxcore/toxcore/group.c
    c-toxcore/toxcore/LAN_discovery.c
    c-toxcore/toxcore/list.c
    c-toxcore/toxcore/logger.c
    c-toxcore/toxcore/Messenger.c
    c-toxcore/toxcore/mono_time.c
    c-toxcore/toxcore/network.c
    c-toxcore/toxcore/net_crypto.c
    c-toxcore/toxcore/onion.c
    c-toxcore/toxcore/onion_announce.c
    c-toxcore/toxcore/onion_client.c
    c-toxcore/toxcore/ping.c
    c-toxcore/toxcore/ping_array.c
    c-toxcore/toxcore/state.c
    c-toxcore/toxcore/TCP_client.c
    c-toxcore/toxcore/TCP_connection.c
    c-toxcore/toxcore/TCP_server.c
    c-toxcore/toxcore/tox.c
    c-toxcore/toxcore/tox_api.c
    c-toxcore/toxcore/util.c
)

target_link_libraries(toxcore
    PRIVATE
        sodium
        $<$<BOOL:WIN32>:
            iphlpapi
            ws2_32
        >
)

add_executable(crypto_test
    c-toxcore/auto_tests/crypto_test.c
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
    c-toxcore/auto_tests/dht_test.c
    c-toxcore/testing/misc_tools.c
)

target_link_libraries(dht_test
    PRIVATE
        toxcore
)

add_test(
    NAME dht_test
    COMMAND dht_test
)
