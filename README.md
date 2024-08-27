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
