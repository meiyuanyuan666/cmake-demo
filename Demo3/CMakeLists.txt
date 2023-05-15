# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

# 项目信息
project (Demo3)

# 查找目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
aux_source_directory(. DIR_SRCS)

# 添加 math 子目录
add_subdirectory(math)

# 指定链接动/静态库
# 我查到了有两个函数link_libraries和target_link_libraries，这两者区别是 前者需放生成目标之前，后者放在生成目标之后。
# link_libraries(${PROJECT_SOURCE_DIR}/libMathFunctions.so)   # 在add_executable前面
# link_libraries(${CMAKE_HOME_DIRECTORY}/libMathFunctions.so)   # 在add_executable前面

# 指定生成目标
add_executable(Demo ${DIR_SRCS})

# 添加链接库
target_link_libraries(Demo MathFunctions)
# target_link_libraries(Demo ${PROJECT_SOURCE_DIR}/libMathFunctions.so)
# target_link_libraries(Demo ${CMAKE_HOME_DIRECTORY}/libMathFunctions.so)

# target_link_libraries(Demo ${PROJECT_SOURCE_DIR}/libMathFunctions.a)
# target_link_libraries(Demo ${CMAKE_HOME_DIRECTORY}/libMathFunctions.a)