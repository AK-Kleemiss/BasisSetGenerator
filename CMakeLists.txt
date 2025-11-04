cmake_minimum_required(VERSION 3.10)
project(BasisSetGenerator VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

file(GLOB SRC_FILES "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp")
add_executable(BasisSetGenerator ${SRC_FILES})

target_include_directories(BasisSetGenerator PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/src
)

if (WIN32)
    set(BSC_EXE "${CMAKE_CURRENT_BINARY_DIR}/BasisSetGenerator.exe")
else ()
    set(BSC_EXE "${CMAKE_CURRENT_BINARY_DIR}/BasisSetGenerator")
endif ()

# Add a release build configuration
set(CMAKE_BUILD_TYPE Release)

# Define the output directory for the executable
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR})


