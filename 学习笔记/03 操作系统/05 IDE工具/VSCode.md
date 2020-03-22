**如何使用本篇文档？**



**规范**

```

```





[TOC]





# 简介

[官网教程](https://code.visualstudio.com/docs/cpp/config-clang-mac)

## 产品公司

微软公司





## 快捷键

Ctrl+Shift+P打开命令面板









# 配置C++

[官方教程](https://code.visualstudio.com/docs/cpp/config-clang-mac)

日期2020-03-11

vs版本1.42.1

从拓展找到C/C++插件，作者是Microsoft

在~/.vscode/extensions/ms-vscode.cpptools目录下有很多文件



**搭建工作开发环境**

创建cpp工作目录，在 工作目录/.vscode/下配置各种文件

接下来的步骤创建三个配置文件

c_cpp_properties.json(编译器路径和IntelliSense设置)

tasks.json(编译命令)

launch.json(调试设置)

```json
c_cpp_properties.json配置方法
打开命令面板，输入c/c++命令(Edit configurations)
然后找到Compiler path，把编译器路径填进去
修改IntelliSense mode为合适的值
大致内容为
{
    "configurations": [
        {
            "name": "Mac",
            "includePath": [
                "${workspaceFolder}/**"
            ],
            "defines": [],
            "macFrameworkPath": [
                "/System/Library/Frameworks",
                "/Library/Frameworks"
            ],
            "compilerPath": "/usr/bin/clang",
            "cStandard": "c11",
            "cppStandard": "c++17",
            "intelliSenseMode": "clang-x64"
        }
    ],
    "version": 4
}
```

```json
task.json文件配置方法 负责程序运行前的生成工作
打开命令面板，输入task，选择Tasks: Configure Task > create tasks.json file from template > others
再选clang build active file
打开tasks.json配置文件
在运行程序之前，按Ctrl+Shift+B进行编译
大概内容为

{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "echo",
            "type": "shell",
            "command": "echo Hello"
        }
    ]
}

args后两项指明要编译的文件,输出的文件
```



```json
launch.json配置文件
打开命令面板，输入launch，选择Debug:Open launch.json
大概内容如下：




其中
```















[vscode配置C++编译环境](https://blog.csdn.net/qq_43041976/article/details/88544632)

[vscode配置C++编译环境 教程](https://blog.csdn.net/qq_43041976/article/details/100542557)



# 单词

schema 计划 概要 提要

properties 属性 性能 道具













