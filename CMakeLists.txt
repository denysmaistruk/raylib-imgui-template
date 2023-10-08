cmake_minimum_required(VERSION 3.18)

project(raylib_imgui_template VERSION 1.0)

# project config
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_CONFIGURATION_TYPES "Debug;Release")
set_property(DIRECTORY PROPERTY VS_STARTUP_PROJECT "raylib_imgui_template")

add_subdirectory(extern/raylib)
add_subdirectory(extern/imgui)

list(APPEND EXTRA_LIBS raylib
                       imgui
                       )
list(APPEND EXTRA_INCLUDES "${PROJECT_SOURCE_DIR}/src"
                           "${PROJECT_SOURCE_DIR}/extern/raylib/src"
                           "${PROJECT_SOURCE_DIR}/extern/imgui/imgui"
                           )

file(GLOB_RECURSE SOURCE_FILES ${PROJECT_SOURCE_DIR}/src/*.cpp ${PROJECT_SOURCE_DIR}/src/*.h)
list(APPEND SOURCE_FILES ${PROJECT_SOURCE_DIR}/main.cpp)

add_executable(raylib_imgui_template ${SOURCE_FILES})

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${SOURCE_FILES})

target_precompile_headers(raylib_imgui_template PUBLIC "${PROJECT_SOURCE_DIR}/src/pch.h")

target_link_libraries(raylib_imgui_template PUBLIC ${EXTRA_LIBS})

target_include_directories(raylib_imgui_template PUBLIC ${EXTRA_INCLUDES})
