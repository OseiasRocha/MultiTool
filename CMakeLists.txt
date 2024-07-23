cmake_minimum_required(VERSION 3.5)

project("MultiTool")

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(SDL2 REQUIRED)
find_package(OpenGL REQUIRED)

include_directories(MultiTool ${SDL2_INCLUDE_DIRS})
include_directories(MultiTool ${OPENGL_INCLUDE_DIRS})
include_directories("./imgui" "./imgui/backends")

file(GLOB IMGUI "./imgui/*.cpp")

add_executable(
  MultiTool
  "MultiTool/main.cpp" "./imgui/backends/imgui_impl_sdl2.cpp"
  "./imgui/backends/imgui_impl_sdlrenderer2.cpp"
  "./imgui/backends/imgui_impl_opengl3.cpp" ${IMGUI})
target_link_libraries(MultiTool ${SDL2_LIBRARIES})
target_link_libraries(MultiTool ${OPENGL_LIBRARIES})
