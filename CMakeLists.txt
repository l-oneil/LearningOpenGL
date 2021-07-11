cmake_minimum_required(VERSION 3.15)
project(opengl_app VERSION 1.0)

set(CMAKE_CXX_FLAGS_DEBUG_INIT "--debug")
set(CMAKE_CXX_FLAGS_RELEASE_INIT "")

# Set Environment Variables
set(glm_DIR "thirdparty/glm/cmake/glm/")

# Third Party Packages 
find_package(glfw3 REQUIRED)
find_package(glm REQUIRED)

# Project Files 
set(INCLUDE_DIRS 
    "src/"
    "thirdparty/stb/"
    "thirdparty/glad/include"
)

set(SRC_FILES 
    "src/main.cpp" 
    "thirdparty/glad/src/glad.c"
)

# Application 
add_executable(${PROJECT_NAME} ${SRC_FILES})
target_include_directories(${PROJECT_NAME} PRIVATE  ${INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} glfw glm::glm)