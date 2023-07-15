# cmake 最低版本
cmake_minimum_required(VERSION 3.22.1)


# 项目名称和语言
project(ProjectName CXX)


# c++ 版本
set(CMAKE_CXX_STANDARD 17)


# 设置路径变量
set(HOME ${CMAKE_CURRENT_SOURCE_DIR})
set(SRC "${HOME}/src")
set(INCLUDE "${HOME}/include")


# include目录, SYSTEM表明是系统头文件 (g++ -I)
include_directories("${INCLUDE}")
include_directories(SYSTEM "/usr/include/")


# 源文件
set (SOURCES
    "main.cpp"
    "test.cpp"
)
# 递归检索src目录下所有源文件, 存储在SOURCES中
aux_source_directory(src SOURCES)


# 显示编译命令
set(CMAKE_VERBOSE_MAKEFILE ON)


# 添加需要链接的库文件 (g++ -L)
link_libraries("/path/to/your/libName")
# 添加需要链接的库文件目录 (g++ -l)
link_directories("path/to/your/libDir")
# 设置要链接的库文件的名称变量
target_link_libraries(LIBNAME "path/to/your/libDir")


# 设置编译器参数 (例如: 增加-g -pthread参数)
add_compile_options(-g -pthread)

# 生成可执行文件
add_executable(${PROJECT_NAME} ${SOURCES})
