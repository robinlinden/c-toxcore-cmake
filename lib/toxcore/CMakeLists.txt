project(toxcore)

find_package(Threads REQUIRED)

set(root ../../c-toxcore/toxcore)

add_library(${PROJECT_NAME}
    ${root}/crypto_core.c
    ${root}/crypto_core_mem.c
    ${root}/DHT.c
    ${root}/friend_connection.c
    ${root}/friend_requests.c
    ${root}/group.c
    ${root}/LAN_discovery.c
    ${root}/list.c
    ${root}/logger.c
    ${root}/Messenger.c
    ${root}/mono_time.c
    ${root}/network.c
    ${root}/net_crypto.c
    ${root}/onion.c
    ${root}/onion_announce.c
    ${root}/onion_client.c
    ${root}/ping.c
    ${root}/ping_array.c
    ${root}/state.c
    ${root}/TCP_client.c
    ${root}/TCP_connection.c
    ${root}/TCP_server.c
    ${root}/tox.c
    ${root}/tox_api.c
    ${root}/util.c
)

target_link_libraries(${PROJECT_NAME}
    PRIVATE
        Threads::Threads
        sodium
        $<$<PLATFORM_ID:Windows>:iphlpapi>
        $<$<PLATFORM_ID:Windows>:ws2_32>
)

# Work around the cmake target not having the same include structure as the installed library.
configure_file(${root}/tox.h ${CMAKE_BINARY_DIR}/toxcore_fix/tox/tox.h)
target_include_directories(${PROJECT_NAME}
    PUBLIC
        ${CMAKE_BINARY_DIR}/toxcore_fix/
)

if(TOXCORE_ENABLE_TESTING)
    add_subdirectory(test)
endif()
