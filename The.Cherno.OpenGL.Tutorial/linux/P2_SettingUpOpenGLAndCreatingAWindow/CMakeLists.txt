cmake_minimum_required(VERSION 3.10)
project(opengl_project LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)

add_executable(application src/Application.cpp)

target_link_libraries(application glfw OpenGL::GL)

