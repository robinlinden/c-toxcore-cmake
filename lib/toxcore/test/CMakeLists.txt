function(make_test name)
    add_executable(${name}
        ${CMAKE_SOURCE_DIR}/c-toxcore/auto_tests/${name}
    )

    target_link_libraries(${name}
        PRIVATE
            toxcore
            toxcore_misc_tools
    )

    add_test(
        NAME ${name}
        COMMAND ${name}
    )
endfunction()

make_test(conference_double_invite_test)
make_test(conference_peer_nick_test)
make_test(conference_simple_test)
make_test(conference_test)
make_test(conference_two_test)
make_test(crypto_test)
make_test(dht_test)
make_test(file_transfer_test)
make_test(friend_connection_test)
make_test(friend_request_test)
make_test(invalid_tcp_proxy_test)
make_test(invalid_udp_proxy_test)
make_test(lan_discovery_test)
make_test(lossless_packet_test)
make_test(lossy_packet_test)
make_test(messenger_test)
make_test(network_test)
make_test(onion_test)
make_test(overflow_recvq_test)
make_test(overflow_sendq_test)
make_test(reconnect_test)
make_test(save_friend_test)
make_test(save_load_test)
make_test(send_message_test)
make_test(set_name_test)
make_test(set_status_message_test)
make_test(skeleton_test)
make_test(TCP_test)
make_test(tox_many_tcp_test)
make_test(tox_many_test)
make_test(tox_one_test)
make_test(tox_strncasecmp_test)
make_test(typing_test)
make_test(version_test)

# TODO(robinlinden):
# make_test(bootstrap_test) the bootstrap node used in 0.2.10 is down.
# make_test(tcp_relay_test) the bootstrap node used in 0.2.10 is down.
# make_test(save_compatibility_test) needs to find its save file.
# make_test(conference_av_test) needs toxav.
# make_test(toxav_basic_test) needs toxav.
# make_test(toxav_many_test) needs toxav.
