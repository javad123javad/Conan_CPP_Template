cmake_minimum_required(VERSION 3.15)

project(CppStack VERSION 0.1 LANGUAGES CXX)

# Library target
add_library(List STATIC List/src/List.cpp)
target_include_directories(List PUBLIC List/include)

# Main executable (no need to link GTest here)
add_executable(${PROJECT_NAME}_bin src/main.cpp)
target_link_libraries(${PROJECT_NAME}_bin PRIVATE List)

# Enable testing once, at the top level
enable_testing()

# Add tests subdirectory
add_subdirectory(tests)