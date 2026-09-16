# Test files
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}")

# Target testing include files
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

add_executable(test_sdl src/test_sdl.cpp)
target_sources(test_sdl PRIVATE src/test_include.cpp)
target_link_libraries(test_sdl PRIVATE ${SDL_LIBS})

add_executable(test_sdl_ttf src/test_sdl_ttf.cpp)
target_link_libraries(test_sdl_ttf PRIVATE ${SDL_LIBS})