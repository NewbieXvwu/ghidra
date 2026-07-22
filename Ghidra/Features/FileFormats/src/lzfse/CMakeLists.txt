cmake_minimum_required(VERSION 3.10)
project(lzfse C)

set(SOURCES
    c/lzfse_main.c
    c/lzfse_encode.c
    c/lzfse_decode.c
    c/lzfse_encode_base.c
    c/lzfse_decode_base.c
    c/lzvn_encode_base.c
    c/lzvn_decode_base.c
    c/lzfse_fse.c
)

add_executable(lzfse ${SOURCES})

if(MSVC)
    target_compile_options(lzfse PRIVATE /O2)
endif()
