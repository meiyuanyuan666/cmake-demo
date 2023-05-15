# 同一目录，多个源文件

# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

# 项目信息
project (Demo2)

# 查找目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
# aux_source_directory(<dir> <variable>)
aux_source_directory(. DIR_SRCS)
# FILE(GLOB DIR_SRCS ${PROJECT_SOURCE_DIR}/*.cc)  # 匹配源码目录所有.cpp文件
# FILE(GLOB_RECURSE DIR_SRCS ${PROJECT_SOURCE_DIR}/*.cc)  # 递归搜索匹配源码目录和其子目录下的.cpp文件

# 指定生成目标
add_executable(Demo ${DIR_SRCS})

# CMake 会将当前目录所有源文件的文件名赋值给变量 DIR_SRCS ，
# 再指示变量 DIR_SRCS 中的源文件需要编译成一个名称为 Demo 的可执行文件。
