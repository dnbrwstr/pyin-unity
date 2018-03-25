cmake_minimum_required(VERSION 3.9)
set(CMAKE_CXX_STANDARD 11)

project(LibPyin)

add_definitions(-DLIBPYIN_BUILD_SHARED)

include_directories(./src/)

aux_source_directory(./src/pyin SRC_LIST)
list(APPEND SRC_LIST ./src/vamp-sdk/FFT.cpp)
list(APPEND SRC_LIST ./src/vamp-sdk/PluginAdapter.cpp)
list(APPEND SRC_LIST ./src/vamp-sdk/RealTime.cpp)

set(CMAKE_BUILD_TYPE Release)

add_library(LibPyin SHARED ${SRC_LIST} ./src/libpyincpp.cpp)
