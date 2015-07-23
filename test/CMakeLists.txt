set(test_SOURCES
    test_main.cpp
    test_huffman.cpp
    test_pack.cpp
    test_unpack.cpp
)

set(test_LIBRARIES
    ${PROGNAME}_core
    ${ZLIB_LIBRARIES}
)

add_executable(${PROGNAME}_test ${test_SOURCES})
target_link_libraries(${PROGNAME}_test
                      ${test_LIBRARIES})

install(TARGETS ${PROGNAME}_test
        BUNDLE DESTINATION . COMPONENT Runtime
        RUNTIME DESTINATION ${BIN_INSTALL_DIR} COMPONENT Runtime)
