cmake_minimum_required(VERSION 3.15)
project(sqlite3 C)

set(SQLITE_SOURCES
    sqlite3.c
)

add_library(sqlite3 SHARED ${SQLITE_SOURCES})

target_include_directories(sqlite3 PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

if (MSVC)
    target_compile_definitions(sqlite3 PRIVATE 
        _CRT_SECURE_NO_WARNINGS=1
        SQLITE_API=__declspec(dllimport)
    )
    
    set_source_files_properties(sqlite3.c PROPERTIES
        COMPILE_DEFINITIONS "SQLITE_API=__declspec(dllexport)"
    )
    
    target_compile_options(sqlite3 PRIVATE 
        /W3
        /O2
        /nologo
    )
    
endif()

set_target_properties(sqlite3 PROPERTIES
    C_STANDARD 99
    C_STANDARD_REQUIRED ON
)

set_target_properties(sqlite3 PROPERTIES
    OUTPUT_NAME "sqlite3"
    PREFIX ""
    RUNTIME_OUTPUT_NAME "sqlite3"
    ARCHIVE_OUTPUT_NAME "sqlite3"
)