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


# 指定头文件目录, SYSTEM表明是系统头文件
include_directories("${INCLUDE}")
include_directories(SYSTEM "/usr/include/")


# 设置每个源文件
set (SOURCES
    "main.cpp"
    "test.cpp"
)
# 递归检索src目录下所有源文件, 存储在SOURCES中
aux_source_directory(src SOURCES)


# 显示编译命令
set(CMAKE_VERBOSE_MAKEFILE ON)


# 添加需要链接的库文件
target_link_libraries("/path/to/your/libName")
# 添加需要链接的库文件目录
target_link_directories("path/to/your/libDir")


# 设置编译器参数 (例如: 增加-g -pthread参数)
add_compile_options(-g -pthread)


# 生成可执行文件
add_executable(${PROJECT_NAME} ${SOURCES})
