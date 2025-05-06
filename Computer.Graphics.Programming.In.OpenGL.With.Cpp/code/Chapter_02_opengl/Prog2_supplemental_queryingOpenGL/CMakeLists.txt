cmake_minimum_required(VERSION 3.10)
project(opengl_example)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)
find_package(GLEW REQUIRED)

add_executable(example main.cpp)

target_link_libraries(example glfw GLEW::GLEW OpenGL::GL)

