include_directories(${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_BINARY_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/..)

if(MINGW)
    set(CMAKE_RC_COMPILER_INIT windres)
    ENABLE_LANGUAGE(RC)
    SET(CMAKE_RC_COMPILE_OBJECT
        "<CMAKE_RC_COMPILER> <FLAGS> -O coff <DEFINES> -i <SOURCE> -o <OBJECT>")
endif(MINGW)

set(bfs2pack_SOURCES
    arg_parser.cpp
    bfs.cpp
    huffman.cpp
    pack.cpp
    unpack.cpp
    XBrowseForFolder.cpp
)
if (WITH_MMGR)
    set(bfs2pack_SOURCES
        ${bfs2pack_SOURCES}
        mmgr.cpp)
endif()

set(bfs2pack_SOURCES_GUI
    main.cpp
    resources.rc
)

set(bfs2pack_SOURCES_CON
    main_console.cpp
)

add_library(${PROGNAME}_core STATIC ${bfs2pack_SOURCES})
set_target_properties(bfs2pack_core PROPERTIES COMPILE_DEFINITIONS BFS2PACK_BUILDING_CORE)

add_executable(${PROGNAME}_gui WIN32 ${bfs2pack_SOURCES_GUI})
target_link_libraries(${PROGNAME}_gui
                      bfs2pack_core
                      ${ZLIB_LIBRARIES})

add_executable(${PROGNAME}_con ${bfs2pack_SOURCES_CON})
target_link_libraries(${PROGNAME}_con
                      ${PROGNAME}_core
                      ${ZLIB_LIBRARIES})

install(TARGETS ${PROGNAME}_gui ${PROGNAME}_con
        BUNDLE DESTINATION . COMPONENT Runtime
        RUNTIME DESTINATION ${BIN_INSTALL_DIR} COMPONENT Runtime)
