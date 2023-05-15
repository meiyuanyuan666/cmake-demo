# 查找当前目录下的所有源文件
# 并将名称保存到 DIR_LIB_SRCS 变量
aux_source_directory(. DIR_LIB_SRCS)
# FILE(GLOB SRCS ${PROJECT_SOURCE_DIR}/*.cc)  # 匹配源码目录所有.cpp文件
# FILE(GLOB_RECURSE SRCS ${PROJECT_SOURCE_DIR}/*.cc )  # 递归搜索匹配源码目录和其子目录下的.cpp文件

# 指定生成 MathFunctions 链接库
# add_library (MathFunctions ${DIR_LIB_SRCS})
# add_library(MathFunctions SHARED ${DIR_LIB_SRCS})		 # 生成libMathFunctions.so
add_library(MathFunctions STATIC ${DIR_LIB_SRCS})  		# 生成libMathFunctions.a

# add_library(hello ${SRCS})
# add_library(hello STATIC ${SRCS})  		# 生成libhello.a
# add_library(hello SHARED ${SRCS})		 # 生成libhello.so
