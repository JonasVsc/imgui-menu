# CMakeList.txt : CMake project for imgui-menu, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("imgui-menu")

find_package(glfw3 CONFIG REQUIRED)
find_package(glew CONFIG REQUIRED)
find_package(glm CONFIG REQUIRED)
find_package(imgui CONFIG REQUIRED)

# Add source to this project's executable.
add_executable (imgui-menu "imgui-menu.cpp" "imgui-menu.h")

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET imgui-menu PROPERTY CXX_STANDARD 20)
endif()

# TODO: Add tests and install targets if needed.

target_link_libraries(imgui-menu PRIVATE glfw)
target_link_libraries(imgui-menu PRIVATE GLEW::glew)
target_link_libraries(imgui-menu PRIVATE glm::glm)
target_link_libraries(imgui-menu PRIVATE imgui::imgui)