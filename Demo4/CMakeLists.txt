# 自定义编译选项
# CMake 允许为项目增加编译选项，从而可以根据用户的环境和需求选择最合适的编译方案。
# 例如，可以将 MathFunctions 库设为一个可选的库，如果该选项为 ON ，
# 就使用该库定义的数学函数来进行运算。否则就调用标准库中的数学函数库。

# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

# 项目信息
project (Demo4)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

# 是否使用自己的 MathFunctions 库
option (USE_MYMATH
	   "Use provided math implementation" OFF)

# configure_file 命令用于加入一个配置头文件 config.h ，这个文件由 CMake 从 config.h.in 生成，
# 通过这样的机制，将可以通过预定义一些参数和变量来控制代码的生成。
# 加入一个配置头文件，用于处理 CMake 对源码的设置
configure_file (
  "${PROJECT_SOURCE_DIR}/config.h.in"
  "${PROJECT_BINARY_DIR}/config.h"
  )

# 是否加入 MathFunctions 库
if (USE_MYMATH)
  include_directories ("${PROJECT_SOURCE_DIR}/math")
  add_subdirectory (math)
  set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
endif (USE_MYMATH)

# 查找当前目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
aux_source_directory(. DIR_SRCS)

# 指定生成目标
add_executable (Demo ${DIR_SRCS})
target_link_libraries (Demo  ${EXTRA_LIBS})

# 编译项目
# 现在编译一下这个项目，为了便于交互式的选择该变量的值，
# 可以使用 ccmake 命令（也可以使用 cmake -i 命令，该命令会提供一个会话式的交互式配置界面）：