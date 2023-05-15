# 单个源文件

# CMakeLists.txt 的语法比较简单，由命令、注释和空格组成，其中命令是不区分大小写的。
# 符号 # 后面的内容被认为是注释。命令由命令名称、小括号和参数组成，参数之间使用空格进行间隔。

# 1、指定运行此配置文件所需的 CMake 的最低版本；
cmake_minimum_required (VERSION 2.8)  #1、cmake版本，必选项。放在第一行，指定cmake最低版本。

# 2、设置工程名字
# 这个应该可以必选项。工程名后面可选 加 语言类型。
# 指定的工程名，在后面可以通过变量${PROJECT_NAME}获取此值。
# 2、参数值是 Demo1，该命令表示项目的名称是 Demo1 。
project (Demo1)

# FILE(GLOB SRCS ${PROJECT_SOURCE_DIR}/*.cc)  # 匹配源码目录所有.cpp文件
# FILE(GLOB_RECURSE SRCS ${PROJECT_SOURCE_DIR}/*.cc )  # 递归搜索匹配源码目录和其子目录下的.cpp文件

# 3、生成可执行文件
# add_executable(可执行文件名 源文件)，源文件可以是变量形式，或者后面加了一串源文件名。
# 3、将名为 main.cc 的源文件编译成一个名称为 Demo 的可执行文件。
add_executable(Demo main.cc)
# add_executable(${PROJECT_NAME} ${SRCS})

# 编译项目
# 之后，在当前目录执行 cmake . ，得到 Makefile 后再使用 make 命令编译得到 Demo1 可执行文件。
