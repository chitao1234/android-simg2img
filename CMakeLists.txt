cmake_minimum_required(VERSION 3.10)

project(libsparse)

find_package(ZLIB REQUIRED)

add_subdirectory(android-base)

add_library(sparse STATIC
            backed_block.cpp
            output_file.cpp
            sparse.cpp
            sparse_crc32.cpp
            sparse_err.cpp
            sparse_read.cpp)
target_link_libraries(sparse PRIVATE base)
target_include_directories(sparse PUBLIC include)

add_executable(simg2img
               simg2img.cpp
               sparse_crc32.cpp)
target_link_libraries(simg2img PRIVATE
                      sparse
                      base
                      ZLIB::ZLIB)

add_executable(append2simg append2simg.cpp)
target_link_libraries(append2simg PRIVATE
                      sparse
                      base
                      ZLIB::ZLIB)

add_executable(img2simg img2simg.cpp)
target_link_libraries(img2simg PRIVATE
                      sparse
                      base
                      ZLIB::ZLIB)