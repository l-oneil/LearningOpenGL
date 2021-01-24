cmake_minimum_required(VERSION 3.15)
project(opengl_app VERSION 1.0)

find_package(glfw3 REQUIRED)

add_executable(${PROJECT_NAME} src/main.cpp thirdparty/glad/src/glad.c)
target_include_directories(${PROJECT_NAME} PRIVATE thirdparty/glad/include)
target_link_libraries(${PROJECT_NAME} glfw)