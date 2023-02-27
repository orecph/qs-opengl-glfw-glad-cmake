cmake_minimum_required(VERSION 3.0.0)
project(testopengl VERSION 0.1.0)

# GLFW
option(GLFW_BUILD_EXAMPLES "Build the GLFW example programs" OFF)
option(GLFW_BUILD_TESTS "Build the GLFW test programs" OFF)
option(GLFW_BUILD_DOCS "Build the GLFW documentation" OFF)
option(GLFW_INSTALL "Generate installation target" OFF)
option(GLFW_DOCUMENT_INTERNALS "Include internals in documentation" OFF)

set(DOXYGEN_SKIP_DOT FALSE)

add_executable(testopengl main.cpp)

set(OpenGL_GL_PREFERENCE GLVND)
find_package(OpenGL REQUIRED)
add_subdirectory(submodules/glfw)

target_include_directories(
    ${PROJECT_NAME}
    PUBLIC submodules/glfw/include
    PUBLIC external/glad/include
)

target_link_directories(
    ${PROJECT_NAME}
    PUBLIC submodules/glfw/src
)

target_link_libraries(
    ${PROJECT_NAME}
    PUBLIC glfw
    PUBLIC ${OPENGL_gl_LIBRARY}
)