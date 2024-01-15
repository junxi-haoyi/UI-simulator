cmake_minimum_required(VERSION 3.0.0)
project(UI-simulator VERSION 0.1.0 LANGUAGES C CXX)

include(CTest)
enable_testing()

add_definitions(-DUSE_SDL)

find_package(PkgConfig REQUIRED)

include_directories(src lvgl/demos)

# 加载子模块
add_subdirectory("lvgl")
add_subdirectory("lv_drivers")

FILE(GLOB_RECURSE src_source ./src/*.c)

add_executable(${PROJECT_NAME} ${src_source})

target_link_libraries(${PROJECT_NAME} lvgl)# add lvgl library to exe
target_link_libraries(${PROJECT_NAME} lv_drivers)# add lv_drivers library to exe
target_link_libraries(${PROJECT_NAME} lvgl_demos)# add lvgl_demos library to exe
target_link_libraries(${PROJECT_NAME} SDL2main)# add SDL2main library to exe
target_link_libraries(${PROJECT_NAME} SDL2)# add SDL2 library to exe

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
