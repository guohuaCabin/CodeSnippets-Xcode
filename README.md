期望：

一套自定义代码片段，可以在不同的设备上通用，一端修改提交后，其他设备拉取代码后执行脚本即可使用最新的自定义代码片段。

### 自定义`CodeSnippets` 

默认文件夹是： 
`~/Library/Developer/Xcode/UserData/CodeSnippets/`

### 系统`CodeSnippets`

默认文件夹是：
`/Applications/Xcode.app/Contents/Frameworks/IDEKit.framework/Versions/A/Resources/SystemCodeSnippets.codesnippets`

思路：

将自己的代码片段创建个代码库，然后设置个软链链接到自定义`CodeSnippets`目标文件夹。



实现脚本：

```shell
#! /bin/bash

## 将原有的自定义代码片段备份
mv ~/Library/Developer/Xcode/UserData/CodeSnippets ~/Library/Developer/Xcode/UserData/CodeSnippets.backup

## 设置软链接到目标文件夹
SRC_HOME=`pwd`
ln -s ${SRC_HOME}/CodeSnippets ~/Library/Developer/Xcode/UserData/CodeSnippets
echo "执行完成！！！"

```

使用：

终端执行 `codesnippets.sh` 脚本文件，实现软链接到自定义`CodeSnippets`目标文件夹。

最后重启`Xcode`即可。