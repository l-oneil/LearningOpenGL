cmake_minimum_required(VERSION 3.15)
project(opengl_app VERSION 1.0)

set(COMMON_FLAGS "-Wno-invalid-offsetof")
set(CMAKE_CXX_FLAGS "${COMMON_FLAGS}")
set(CMAKE_CXX_FLAGS_DEBUG_INIT "--debug ${COMMON_FLAGS}")
set(CMAKE_CXX_FLAGS_RELEASE_INIT "${COMMON_FLAGS}")

# Third Party Packages
find_package(glfw3 REQUIRED)
find_package(glm REQUIRED PATHS "thirdparty/glm/cmake/glm/")
#TODO: fix this hack, assimp needs to be compiled separately inside: `thirdparty/assimp/build/`
add_library(assimp SHARED IMPORTED)
set_target_properties(assimp PROPERTIES
  IMPORTED_LOCATION "${CMAKE_SOURCE_DIR}/thirdparty/assimp/build/code/libassimp.dylib"
  INTERFACE_INCLUDE_DIRECTORIES "${CMAKE_SOURCE_DIR}/thirdparty/assimp/include"
)

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
target_link_libraries(${PROJECT_NAME} glfw glm::glm assimp)