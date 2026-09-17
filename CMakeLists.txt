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



# Set include directories
include_directories(${CMAKE_SOURCE_DIR}/include)

# Add all main project source files here
file(GLOB SRC src/*cpp)


# Set external libraries
add_subdirectory(external/SDL EXCLUDE_FROM_ALL)
add_subdirectory(external/SDL_ttf EXCLUDE_FROM_ALL)
add_subdirectory(external/SDL_image EXCLUDE_FROM_ALL)
add_subdirectory(external/SDL_mixer EXCLUDE_FROM_ALL)
add_subdirectory(external/SDL_net EXCLUDE_FROM_ALL)

set(SDL_LIBS SDL3_ttf::SDL3_ttf SDL3_image::SDL3_image SDL3_mixer::SDL3_mixer SDL3_net::SDL3_net SDL3::SDL3)


# Create Main Executable
add_executable(${CMAKE_PROJECT_NAME} src/main.cpp)
target_sources(${CMAKE_PROJECT_NAME} PRIVATE ${SRC})
target_link_libraries(${CMAKE_PROJECT_NAME} PRIVATE ${SDL_LIBS})


# Create Test Executables
add_subdirectory(test)



