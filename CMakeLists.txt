cmake_minimum_required(VERSION 3.17)
project(edu_opengl)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror")

set(source_dir "${PROJECT_SOURCE_DIR}/src")
file(GLOB source_files "${source_dir}/*.cpp")

set(GLFW_BUILD_DOCS OFF CACHE BOOL "")
set(GLFW_BUILD_TESTS OFF CACHE BOOL "")
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "")
set(GLFW_INSTALL OFF CACHE BOOL "")

add_subdirectory(dependencies/GLFW)

add_executable(edu_opengl MACOSX_BUNDLE ${source_files})
target_link_libraries(edu_opengl glfw)

find_package(OpenGL REQUIRED)
target_include_directories(edu_opengl SYSTEM PRIVATE ${OPENGL_INCLUDE_DIR})
target_link_libraries(edu_opengl ${OPENGL_gl_LIBRARY})
