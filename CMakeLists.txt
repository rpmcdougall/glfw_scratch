#cmake_minimum_required(VERSION 3.12)
#project(glfw_scratch)
#
#set(${CMAKE_CXX_FLAGS} -lglfw -lglew -framework OpenGL)
#
#set(CMAKE_CXX_STANDARD 14)
#
#find_package(OpenGL REQUIRED)
#find_package(GLEW REQUIRED)
#find_package(glfw3 3.2 REQUIRED)
#
#
#include_directories(${GLEW_INCLUDE_DIRS})
#link_libraries(${GLEW_LIBRARY})
#
#include_directories(${GLFW_INCLUDE_ES3})
#link_libraries(${GLFW_LIBRARY})
#
#target_include_directories(glfw_scratch ${OPENGL_INCLUDE_DIR})
#target_link_libraries(glfw_scratch glfw)
##add_executable(glfw_scratch main.cpp)


cmake_minimum_required(VERSION 3.12)
project(glfw_scratch)


set (CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

set(CMAKE_CXX_STANDARD 14)
set(${CMAKE_CXX_FLAGS} -lglfw -lglew -lgl -framework OpenGL)

find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED)

include_directories(${GLFW_INCLUDE_ES3})
link_libraries(${GLFW_LIBRARY})

include_directories(${OpenGL_INCLUDE_DIRS})
link_libraries(${OPENGL_LIBRARIES})


include_directories(${GLEW_INCLUDE_DIRS})
link_libraries(${GLEW_LIBRARIES})


file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/shaders
        DESTINATION ${CMAKE_CURRENT_BINARY_DIR})

add_executable(glfw_scratch main.cpp ShaderUtils.h)
target_link_libraries(glfw_scratch glfw ${GLEW_LIBRARIES})