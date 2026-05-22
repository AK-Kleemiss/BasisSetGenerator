
cmake_minimum_required(VERSION 3.10)
project(BasisSetConverter VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Simple single-executable project (no generation step)
set(SRC_DIR ${CMAKE_CURRENT_SOURCE_DIR})
set(SOURCES
    ${SRC_DIR}/src/basis_set_helper.cpp
    ${SRC_DIR}/src/BasisSetConverter.cpp
)

add_executable(BasisSetConverter ${SOURCES})

target_include_directories(BasisSetConverter PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/src
)

# Prefer target-level language requirement
target_compile_features(BasisSetConverter PUBLIC cxx_std_17)

# Sensible warnings per-compiler
if(MSVC)
    target_compile_options(BasisSetConverter PRIVATE /W4)
else()
    target_compile_options(BasisSetConverter PRIVATE -Wall -Wextra -Wpedantic)
endif()

message(STATUS "Configuring single-executable project 'BasisSetConverter'")

