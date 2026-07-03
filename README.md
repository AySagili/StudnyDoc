# StudnyDoc

学习文档

## 规范命名

我这边统一是用大驼峰表示函数  
例如以下

```C++
MyFirstFunction(){
...
}
```

下划线小写连字作为参数和变量

```C++
MyFirstFunction(int a_b_c){
    a_b_c ...
}
```

### 字体安装网址

https://www.nerdfonts.com/font-downloads

### 安装 WSL2 到除了 C 盘以外的位置

### 改变 windows docker 终端没有颜色的问题

```
在/etc/bash.bashrc 文件末尾添加
#shell color style setting

export PS1="\[\e[36m\]\u\[\e[m\]@\[\e[32m\]\h\[\e[m\]:\[\e[33m\]\w\[\e[m\]\$ "

export GREP_OPTIONS='--color=auto'
export GREP_COLOR='1;35'
alias ls='ls --color=auto'

export LESS_TERMCAP_mb=$'\E[01;31m'
export LESS_TERMCAP_md=$'\E[01;31m'
export LESS_TERMCAP_me=$'\E[0m'
export LESS_TERMCAP_se=$'\E[0m'
export LESS_TERMCAP_so=$'\E[01;44;33m'
export LESS_TERMCAP_ue=$'\E[0m'
export LESS_TERMCAP_us=$'\E[01;32m'
```

https://blog.csdn.net/xc18113397842/article/details/132637528?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0-132637528-blog-132202467.235^v43^pc_blog_bottom_relevance_base1&spm=1001.2101.3001.4242.1&utm_relevant_index=3

### 修复 WSLG 中 GUI 不显示中文的情况 在容器内输入以下命令

Fedora  
sudo yum install wqy-microhei-fonts wqy-zenhei-fonts  
sudo dnf install fontconfig  
在/root/.bashrc 末尾增加以下两行  
export LANG=zh_CN.UTF-8
export LC_ALL=zh_CN.UTF-8  
输入  
source ~/.bashrc  
fc-cache -fv  
即可


1、你平时用哪个AI 工具写代码？（Trae/ Codex/ Cursor/ Copilot 等），用了多久？依赖程度大概多少比如30%、50%、80%的代码靠AI 生成？
答：Claude Code、Open Code（终端类的AI构建工具，现阶段也有可视化插件可以使用），Trae也有用过，本质上个人感觉就是多了个IDE的功能,如果从学校算起（Vscode的AI构建插件），西山居实习期间（前面讲述过）用了三年多了，实习工作期间使用了七个多月，根据不同工作需求的复杂度依赖从60%到90%不等。
2、有没有完全靠自己从O 到1完成过项目？简单说一下是什么项目、做了什么。
答：阳光岛（SDL3全家桶）实现的引擎（Engine）和游戏逻辑分离的2D跑酷游戏，co_async（基于Linux io_uring 纯异步驱动和C++20的协程特性实现的异步库，包括文件流，网络流和HTTP框架），工作内容由于签了保密协议，所以没办法讲述。
自问：为什么还要多次一举写一个市面上已经烂大街的异步库
答：大部分都是基于Epoll实现的异步，这种只是属于伪异步（依旧会阻塞主线程），写co_async是为了学习协程和现代Linux的异步特性（io_uring 双环形队列实现真正的异步），HTTP框架也是为了学习Spring，Gin等框架的底层实现（co_async使用了和Gin一样的基于基数树所实现的路由模块）
3、如果项目上线前有bug没修完，你愿意加班搞定吗？能接受什么程度的加班？
答：完全可以加班搞定，目前在实习期间我误打误撞被分到了一个年前就要上线的项目，当初是九月份进入实习，一直到项目后一周（项目上线需要有人负责随时待命），基本每天都是网上9-10点，偶尔紧急的任务可能是直接通宵。
4、（加分项）除了 Vue，还会不会后端？Java/Python/Node都行，说一下水平。
答：后端会使用Spring全家桶，Python的Flask，Golang的Gin框架，完成工作任务肯定是没问题的，再加上目前AI这么发达，我觉得通过AI去快速上手和使用工作所需要的技能才是比较重要的


