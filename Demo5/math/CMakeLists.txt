# 查找当前目录下的所有源文件
# 并将名称保存到 DIR_LIB_SRCS 变量
aux_source_directory(. DIR_LIB_SRCS)

# 指定生成 MathFunctions 链接库
add_library (MathFunctions ${DIR_LIB_SRCS})

# 指定 MathFunctions 库的安装路径
# 生成的 Demo 文件和 MathFunctions 函数库 libMathFunctions.o 文件将会被复制到 /usr/local/bin 中
install (TARGETS MathFunctions DESTINATION lib)
# 而 MathFunctions.h 和生成的 config.h 文件则会被复制到 /usr/local/include 中
install (FILES MathFunctions.h DESTINATION include)


# 安装可执行文件
# install(TARGETS ${PROJECT_NAME} RUNTIME DESTINATION bin)  # 安装在 /usr/local/bin目录

# 安装动态库到lib目录
# install(TARGETS ${PROJECT_NAME} LIBRARY DESTINATION lib)  # 安装在 /usr/local/lib目录
# install(TARGETS ${PROJECT_NAME} ARCHIVE DESTINATION lib)  # 多用于静态库

# 安装对外头文件
# install(TARGETS ${XXXX} PUBLIC_HEADER DESTINATION include)

# 安装其他文件，比如配置文件
# install(FILES ${CONFIGS} DESTINATION config)


# 顺带一提的是，这里的 /usr/local/ 是默认安装到的根目录，可以通过修改 CMAKE_INSTALL_PREFIX 变量的值来指定这些文件应该拷贝到哪个根目录
