cmake_minimum_required(VERSION 3.27)
project(gbRPG)

set(CMAKE_CXX_STANDARD 17)
find_package(Vulkan REQUIRED)

add_subdirectory(Lib/glfw-3.4 EXCLUDE_FROM_ALL)
SET(GLM_TEST_ENABLE OFF CACHE BOOL "GLM Build unit tests")
add_subdirectory(Lib/glm-1.0.1 EXCLUDE_FROM_ALL)

add_executable(${PROJECT_NAME} main.cpp)

# add shaders files
file(COPY shaders DESTINATION ${CMAKE_CURRENT_BINARY_DIR})

target_link_libraries(${PROJECT_NAME} glfw ${GLFW_LIBRARIES} Vulkan::Vulkan glm::glm)

