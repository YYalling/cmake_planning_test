cmake_minimum_required(VERSION 3.29.0)
project(planning)
set(CMAKE_CXX_STANDARD 17)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
aux_source_directory(. SRC_LISTS) #.的作用是当前文件夹下的所有文件
add_executable(planning_main ${SRC_LISTS})