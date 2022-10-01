cmake_minimum_required(VERSION 3.18)

project(imgui VERSION 1.87)

file(GLOB SOURCE_FILES ${CMAKE_CURRENT_SOURCE_DIR}/imgui/*.cpp
                       ${CMAKE_CURRENT_SOURCE_DIR}/imgui/*.h)

add_library(imgui ${SOURCE_FILES})