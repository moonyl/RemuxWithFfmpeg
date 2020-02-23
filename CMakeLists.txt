cmake_minimum_required(VERSION 3.15)
project(RemuxWithFfmpeg)

set(CMAKE_CXX_STANDARD 14)

add_library(avformat SHARED IMPORTED)
add_library(avutil SHARED IMPORTED)
add_library(avcodec SHARED IMPORTED)

set_target_properties(avformat PROPERTIES
        IMPORTED_IMPLIB ${CMAKE_CURRENT_SOURCE_DIR}/ffmpeg-4.2.2-win64-dev/lib/avformat.lib
        IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/ffmpeg-4.2.2-win64-dev/bin/avformat-58.dll)

set_target_properties(avutil PROPERTIES
        IMPORTED_IMPLIB ${CMAKE_CURRENT_SOURCE_DIR}/ffmpeg-4.2.2-win64-dev/lib/avutil.lib
        IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/ffmpeg-4.2.2-win64-dev/bin/avutil-56.dll)

set_target_properties(avcodec PROPERTIES
        IMPORTED_IMPLIB ${CMAKE_CURRENT_SOURCE_DIR}/ffmpeg-4.2.2-win64-dev/lib/avcodec.lib
        IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/ffmpeg-4.2.2-win64-dev/bin/avcodec-58.dll)

set_target_properties(avformat avutil avcodec PROPERTIES
        INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_SOURCE_DIR}/ffmpeg-4.2.2-win64-dev/include
        INTERFACE_COMPILE_DEFINITIONS __STDC_CONSTANT_MACROS)

add_executable(RemuxWithFfmpeg main.cpp)
target_link_libraries(RemuxWithFfmpeg PRIVATE avformat avutil avcodec)