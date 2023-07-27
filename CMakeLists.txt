cmake_minimum_required(VERSION 3.14)

project(catch2Subdir)

add_subdirectory(external/Catch2/v3.4.0)
add_subdirectory(src)
