# BUG 记录

## Linux 这边的 MySQL Connector/C++

### 2024/8/16

大致情况是出现找不到 check() 但是这个 check 里面有个关键字就是 lib  
所以不难看出是没有链接库的问题

g++ main.cpp -o mysql_example -lmysqlcppconn  
cmake 的话链接一下就行  
但是奇怪的情况是 同样的代码 同样的 cmake 配置 同样的系统 只是不同的文件夹  
一个可以成功运行 一个不可以，但是不知道为啥 突然两个都可以了 奇了怪了  
记录一下

## windows 那边的还没解决
