project(toxcore)

set(ROOT ${CMAKE_SOURCE_DIR}/c-toxcore)

add_library(${PROJECT_NAME}
    ${ROOT}/toxcore/crypto_core.c
    ${ROOT}/toxcore/crypto_core_mem.c
    ${ROOT}/toxcore/DHT.c
    ${ROOT}/toxcore/friend_connection.c
    ${ROOT}/toxcore/friend_requests.c
    ${ROOT}/toxcore/group.c
    ${ROOT}/toxcore/LAN_discovery.c
    ${ROOT}/toxcore/list.c
    ${ROOT}/toxcore/logger.c
    ${ROOT}/toxcore/Messenger.c
    ${ROOT}/toxcore/mono_time.c
    ${ROOT}/toxcore/network.c
    ${ROOT}/toxcore/net_crypto.c
    ${ROOT}/toxcore/onion.c
    ${ROOT}/toxcore/onion_announce.c
    ${ROOT}/toxcore/onion_client.c
    ${ROOT}/toxcore/ping.c
    ${ROOT}/toxcore/ping_array.c
    ${ROOT}/toxcore/state.c
    ${ROOT}/toxcore/TCP_client.c
    ${ROOT}/toxcore/TCP_connection.c
    ${ROOT}/toxcore/TCP_server.c
    ${ROOT}/toxcore/tox.c
    ${ROOT}/toxcore/tox_api.c
    ${ROOT}/toxcore/util.c
)

target_link_libraries(${PROJECT_NAME}
    PRIVATE
        sodium
        $<$<BOOL:WIN32>:
            iphlpapi
            ws2_32
        >
)

if(TOXCORE_ENABLE_TESTING)
    add_subdirectory(test)
endif()
