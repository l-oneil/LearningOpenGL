cmake_minimum_required(VERSION 3.15)
project(opengl_app VERSION 1.0)

set(CMAKE_CXX_FLAGS_DEBUG_INIT "--debug")
set(CMAKE_CXX_FLAGS_RELEASE_INIT "")

# Third Party Packages 
find_package(glfw3 REQUIRED)
find_package(glm REQUIRED PATHS "thirdparty/glm/cmake/glm/")

# Project Files 
set(INCLUDE_DIRS 
    "src/"
    "thirdparty/stb/"
    "thirdparty/glad/include"
    "thirdparty/imgui/"
    "thirdparty/imgui/backends"
)

set(SRC_FILES 
    "src/main.cpp" 
    "thirdparty/glad/src/glad.c"
    "thirdparty/imgui/imgui.cpp"
    "thirdparty/imgui/imgui_draw.cpp"
    "thirdparty/imgui/imgui_tables.cpp"
    "thirdparty/imgui/imgui_widgets.cpp"
    "thirdparty/imgui/backends/imgui_impl_opengl3.cpp"
    "thirdparty/imgui/backends/imgui_impl_glfw.cpp"
)

# Application 
add_executable(${PROJECT_NAME} ${SRC_FILES})
target_include_directories(${PROJECT_NAME} PRIVATE  ${INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} glfw glm::glm)