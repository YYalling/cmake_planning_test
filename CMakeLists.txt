cmake_minimum_required(VERSION 3.29.0) #项目版本
project(planning) #项目名称
set(CMAKE_CXX_STANDARD 17) #设置c++版本在17以上

# 让生成的动态库和执行文件一个文件夹下面，意思：让dll和exe都在bin文件夹下
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)

# 项目执行文件生成的目录
#set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin) 

# .的作用是当前文件夹下的所有文件
#aux_source_directory(. SRC_LISTS) 

# 将cpp文件打包
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS) 
# 生成动态库名字为common 和可执行文件放在一个目录dll与exe在一起
add_library(common
SHARED
${SRC_LISTS}
) 
# 生成的动态库要依赖的头文件位置
target_include_directories(common
PUBLIC
${PROJECT_SOURCE_DIR}/include
) 

# planning_main为可执行文件名，可执行文件依赖planning_main.cpp 
add_executable(planning_main planning_main.cpp) 

# 生成的可执行文件要依赖的头文件位置
target_include_directories(planning_main
PUBLIC
${PROJECT_SOURCE_DIR}/include
) 

# 生成的可执行文件要来链接动态库
target_link_libraries(planning_main
PUBLIC
common
) 