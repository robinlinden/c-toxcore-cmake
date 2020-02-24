include(FetchContent)

FetchContent_Declare(libsodium
    GIT_REPOSITORY https://github.com/robinlinden/libsodium-cmake
    GIT_TAG b2b73fcd8c73c9ed6e4452a40763ce75dbe730d2 # 1.0.18
)

set(SODIUM_DISABLE_TESTS
        ON CACHE INTERNAL "")
set(SODIUM_MINIMAL
        OFF CACHE INTERNAL "")
set(SODIUM_PRETEND_TO_BE_CONFIGURED
        ON CACHE INTERNAL "")

FetchContent_MakeAvailable(libsodium)
