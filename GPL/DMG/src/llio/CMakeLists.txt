cmake_minimum_required(VERSION 3.10)
project(llio C)

set(SOURCES
    c/llio_common.c
    c/org_catacombae_hfsexplorer_win32_WindowsLowLevelIO.c
    c/org_catacombae_hfsexplorer_win32_WritableWin32File.c
)

add_library(llio_arm64 SHARED ${SOURCES})

target_compile_definitions(llio_arm64 PRIVATE
    WINDOWS
    _WINDOWS
    WIN32
    _WIN32
    _CRT_SECURE_NO_DEPRECATE
    _CRT_NONSTDC_NO_DEPRECATE
)

if(DEFINED JAVA_HOME)
    target_include_directories(llio_arm64 PRIVATE
        ${JAVA_HOME}/include
        ${JAVA_HOME}/include/win32
    )
endif()

if(MSVC)
    target_compile_options(llio_arm64 PRIVATE /O2)
endif()
