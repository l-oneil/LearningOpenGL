cmake_minimum_required(VERSION 3.15)
project(opengl_app VERSION 1.0)

# Set Environment Variables
set(glm_DIR "thirdparty/glm/cmake/glm/")

# Third Party Packages 
find_package(glfw3 REQUIRED)
find_package(glm REQUIRED)

# Application 
add_executable(${PROJECT_NAME} "src/main.cpp" "thirdparty/glad/src/glad.c")
target_include_directories(${PROJECT_NAME} PRIVATE "src/" "thirdparty/glad/include")
target_link_libraries(${PROJECT_NAME} glfw glm::glm)