# TODO 1: Set the minimum required version of CMake to be 3.10
cmake_minimum_required(VERSION 3.10)

# TODO 2: Create a project named Tutorial
# 在设置项目的版本号的同时，变量Tutorial_VERSION_MINOR和Tutorial_VERSION_MAJOR被隐式地设置好了
project(Tutorial VERSION 1.0)

# TODO 7: Set the project version number as 1.0 in the above project command

# TODO 6: Set the variable CMAKE_CXX_STANDARD to 11
#         and the variable CMAKE_CXX_STANDARD_REQUIRED to True
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# TODO 8: Use configure_file to configure and copy TutorialConfig.h.in to
#         TutorialConfig.h
# 在cmake中，下面这一函数用于将一个输入文件处理后生成一个输出文件。在输入文件（即TutorialConfig.h.in）中通常包含占位符（@var@），在从h.in到h的转换中，这个占位符会被替换为实际的值。
# 一般生成的输出文件会放在build目录中，改路径也没用，强制放在build目录中
configure_file("./TutorialConfig.h.in" "TutorialConfig.h")

# TODO 3: Add an executable called Tutorial to the project
# Hint: Be sure to specify the source file as tutorial.cxx
add_executable(Tutorial "./tutorial.cxx")

# TODO 9: Use target_include_directories to include ${PROJECT_BINARY_DIR}
# 在利用configure_file函数将（源文件目录中的）输入文件转换为(一般要放在在build目录中的)头文件之后，要用到这个头文件，就要把这个头文件所在的目录路径包含进来，总之这个目录也是build目录啦
target_include_directories(Tutorial PUBLIC "${PROJECT_BINARY_DIR}")
