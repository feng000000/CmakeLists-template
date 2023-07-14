# 指定 cmake 最低版本
cmake_minimum_required(VERSION 3.22.1)

# 指定项目名称和语言
project(ProjectName CXX)

# 设置 c++ 版本
set(CMAKE_CXX_STANDARD 17)

# 设置项目路径
set(HOME ${CMAKE_CURRENT_SOURCE_DIR})
set(SRC "${HOME}/src")
set(INCLUDE "${HOME}/include")
set(DEPENDENCIES "${HOME}/dependencies")

# 设置链接选项
# PROJECT_NAME是项目名称
# libname是需要链接的库文件名称
target_link_libraries(${PROJECT_NAME} "${DEPENDENCIES}/libname")

# 设置编译器参数 (例如: 增加-g -pthread参数)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} lpthread")

# 递归检索目录下所有源文件
aux_source_directory(src SRCS)

# 指定头文件目录, SYSTEM表明是系统头文件
include_directories("${INCLUDE}")
include_directories(SYSTEM "/usr/include/")

# 生成可执行文件
add_executable(${PROJECT_NAME} ${SRCS})
