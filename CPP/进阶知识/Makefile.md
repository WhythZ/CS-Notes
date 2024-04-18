# 1 在Linux中的使用
- 安装编译器gcc以及gcc-c++
```
sudo yum install gcc gcc-c++
```
- 安装Makefile需要的make以及cmake
```
sudo yum install make cmake
```
- 为项目创建一个根目录文件夹`testcpp`，设子文件夹`src`和`include`，`src`存放主程序源文件`main.cpp`以及写入函数定义的源文件`func.cpp`，`include`存放写入函数声明的头文件`func.h`，确认代码书写无误后，在根目录创建一个名为`Makefile`的文件，用vim编辑器打开写入如下代码
```
# 编译器
CC = g++

# 编译选项
CFLAGS = -Wall -g

# 目标文件夹
TARGET_DIR = bin

# 可执行文件名
TARGET = $(TARGET_DIR)/main

# 源文件夹
SRC_DIR = src

# 头文件文件夹
INC_DIR = include

# 目标文件夹
OBJ_DIR = obj

# 所有源文件
SRCS = $(wildcard $(SRC_DIR)/*.cpp)

# 所有对象文件
OBJS = $(patsubst $(SRC_DIR)/%.cpp, $(OBJ_DIR)/%.o, $(SRCS))

# 所需头文件路径
INC = -I$(INC_DIR)

# 默认目标
all: $(TARGET)

# 生成目标文件夹
$(TARGET_DIR):
    mkdir -p $(TARGET_DIR)

# 生成对象文件夹
$(OBJ_DIR):
    mkdir -p $(OBJ_DIR)

# 编译目标文件
$(OBJ_DIR)/%.o: $(SRC_DIR)/%.cpp | $(OBJ_DIR)
    $(CC) $(CFLAGS) $(INC) -c $< -o $@

# 生成可执行文件
$(TARGET): $(OBJS) | $(TARGET_DIR)
    $(CC) $(CFLAGS) $(OBJS) -o $(TARGET)

# 清理操作
clean:
    rm -rf $(TARGET_DIR) $(OBJ_DIR)

# 避免与文件同名的伪目标
.PHONY: all clean
```
- 然后在根目录中用指令`./bin/main`运行make后生成的bin中的main可执行文件，就能运行程序了