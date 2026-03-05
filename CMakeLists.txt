cmake_minimum_required(VERSION 3.5)

project(HelloRaylib)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(FetchContent)

#get raylib
FetchContent_Declare(raylib
 GIT_REPOSITORY https://github.com/raysan5/raylib
 GIT_TAG 5.5)
FetchContent_GetProperties(raylib)

if(NOT raylib_POPULATED)
 FetchContent_Populate(raylib)
 add_subdirectory(${raylib_SOURCE_DIR} ${raylib_BUILD_DIR})
endif()



include_directories(${raylib_SOURCE_DIR})

add_executable(main_window main_window.cpp)
add_executable(main_mouse main_mouse.cpp)
add_executable(main_keys main_keys.cpp)
add_executable(main_platform main_platform.cpp)

target_link_libraries(main_window raylib)
target_link_libraries(main_mouse raylib)
target_link_libraries(main_keys raylib)
target_link_libraries(main_platform raylib)

