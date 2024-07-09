cmake_minimum_required(VERSION 3.10)

project(libbase)

add_library(base STATIC
            mapped_file.cpp
            stringprintf.cpp)
target_include_directories(base PUBLIC include)
