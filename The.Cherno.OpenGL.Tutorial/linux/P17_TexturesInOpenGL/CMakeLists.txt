cmake_minimum_required(VERSION 3.10)
project(opengl_project LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# copy res/shaders
set(SHADER_FILES Basic.shader)

foreach(file ${SHADER_FILES})
    add_custom_command(
        OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/res/shaders/${file}
        COMMAND ${CMAKE_COMMAND} -E make_directory ${CMAKE_CURRENT_BINARY_DIR}/res/shaders
        COMMAND ${CMAKE_COMMAND} -E copy
                ${CMAKE_CURRENT_SOURCE_DIR}/res/shaders/${file}
                ${CMAKE_CURRENT_BINARY_DIR}/res/shaders/${file}
        DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/res/shaders/${file}
        COMMENT "Copying shader file ${file}"
    )
endforeach()

# copy res/textures
set(TEXTURES_FILES ChernoLogo.png)

foreach(file ${TEXTURES_FILES})
    add_custom_command(
        OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/res/textures/${file}
        COMMAND ${CMAKE_COMMAND} -E make_directory ${CMAKE_CURRENT_BINARY_DIR}/res/textures
        COMMAND ${CMAKE_COMMAND} -E copy
                ${CMAKE_CURRENT_SOURCE_DIR}/res/textures/${file}
                ${CMAKE_CURRENT_BINARY_DIR}/res/textures/${file}
        DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/res/textures/${file}
        COMMENT "Copying texture file ${file}"
    )
endforeach()

add_custom_target(copy_files ALL
    DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/res/shaders/Basic.shader
    DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/res/textures/ChernoLogo.png
)

find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)
find_package(GLEW REQUIRED)

add_subdirectory(src/vendor/stb_image)

add_executable(application
    src/Application.cpp
    src/IndexBuffer.cpp
    src/IndexBuffer.h
    src/Renderer.cpp
    src/Renderer.h
    src/Shader.cpp
    src/Shader.h
    src/Texture.cpp
    src/Texture.h
    src/VertexArray.cpp
    src/VertexArray.h
    src/VertexBuffer.cpp
    src/VertexBuffer.h
    src/VertexBufferLayout.h
)

target_link_libraries(application glfw GLEW::GLEW OpenGL::GL stb_image)

add_dependencies(application copy_files)
