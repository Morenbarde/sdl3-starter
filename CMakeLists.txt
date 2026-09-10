cmake_minimum_required(VERSION 3.16)

# Project name
project(sdl3-starter)

###############
# C++ Options #
###############
# set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++20")
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# set the output directory for built objects.
# This makes sure that the dynamic library goes into the build directory automatically.
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/$<CONFIGURATION>")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/$<CONFIGURATION>")


add_subdirectory(external/SDL EXCLUDE_FROM_ALL)

# Set include directories
include_directories(${CMAKE_SOURCE_DIR}/include)

# Get source files
file(GLOB SRC src/*cpp)

# Create Executables
add_executable(${PROJECT_NAME} src/main.cpp)

# Target source files
target_sources(${PROJECT_NAME} PRIVATE ${SRC})

# Link external libraries
target_link_libraries(${PROJECT_NAME} PRIVATE SDL3::SDL3)