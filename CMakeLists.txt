cmake_minimum_required(VERSION 3.20)
project(OGL)

set(CMAKE_CXX_STANDARD 14)

# 添加头文件
set(GLEW_H /usr/local/Cellar/glew/2.2.0_1/include/GL)
set(GLFW_H /usr/local/Cellar/glfw/3.3.4/include/GLFW)
set(GLM_H /usr/local/Cellar/glm/0.9.9.8/include/glm)
include_directories(${GLEW_H} ${GLFW_H} ${GLM_H})
include_directories(${PROJECT_SOURCE_DIR})

# 添加目标链接
set(GLEW_LINK /usr/local/Cellar/glew/2.2.0_1/lib/libGLEW.2.2.0.dylib)
set(GLFW_LINK /usr/local/Cellar/glfw/3.3.4/lib/libglfw.3.3.dylib)
link_libraries(${OPENGL} ${GLEW_LINK} ${GLFW_LINK})

# User playground
add_executable(playground
        playground/playground.cpp
        )

add_executable(tutorial01
        tutorial01_first_window/tutorial01.cpp
        )

add_executable(tutorial07
        tutorial07_model_loading/tutorial07.cpp
        common/shader.cpp
        common/controls.cpp
        common/texture.cpp
        common/objloader.cpp
        )

# Tutorial 8
add_executable(tutorial08
        tutorial08_basic_shading/tutorial08.cpp
        common/shader.cpp
        common/controls.cpp
        common/texture.cpp
        common/objloader.cpp
        common/vboindexer.cpp
        )

if (APPLE)
    target_link_libraries(playground "-framework OpenGL")
    target_link_libraries(playground "-framework GLUT")
    target_link_libraries(tutorial01 "-framework OpenGL")
    target_link_libraries(tutorial01 "-framework GLUT")
    target_link_libraries(tutorial07 "-framework OpenGL")
    target_link_libraries(tutorial07 "-framework GLUT")
    target_link_libraries(tutorial08 "-framework OpenGL")
    target_link_libraries(tutorial08 "-framework GLUT")
endif()