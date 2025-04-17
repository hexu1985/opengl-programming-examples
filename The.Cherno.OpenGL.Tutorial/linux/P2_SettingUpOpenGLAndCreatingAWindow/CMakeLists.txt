cmake_minimum_required(VERSION 3.10)
project(glfw_example)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)

add_executable(glfw_example src/Application.cpp)

target_link_libraries(glfw_example glfw OpenGL::GL)

# 安装GLFW（如果使用源码编译）
# 或者使用以下命令安装：
# sudo apt-get install libglfw3 libglfw3-dev
