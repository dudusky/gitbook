# GitBook协同办公流程

## 目的

> 团队协同编写技术文档
* 版本管理
* 协同办公
* 资源共享
* 统一规范




## 安装工具

* Github

  * 创建个人账户

  * 创建仓库

    ​

* Gitbook

  * 下载地址 https://www.gitbook.com/editor




## 基本配置

* 配置Gitbook和Github

  * 安装Github集成Gitbook
  * 共享仓库
  * 截图演示

  ​

## 编辑书籍

> 在创建了书籍后，可以使用免费的在线编辑器进行编辑，也可以使用 [gitbook editor](https://github.com/GitbookIO/editor) 编辑，甚至使用任何喜欢的文本编辑器来编辑.



### 克隆书籍源代码

GitBook.com 上的每本书都使用 Git 项目来管理，所以，这里首先需要克隆需要编辑书籍的 Git 项目，登陆 GitBook.com 后，跳转到书籍的属性页面，如下图所示：



点击 "Edit Book" 上方的 "learn more"，将会展现此书籍的 Git 项目地址，以及简单的使用方法，如下图所示：





使用如下命令，克隆书籍的源代码：

```
$ git clone https://github.com/dudusky/gitbook.git
Cloning into 'test'...
remote: Counting objects: 28, done.
remote: Compressing objects: 100% (17/17), done.
remote: Total 28 (delta 6), reused 28 (delta 6)
Unpacking objects: 100% (28/28), done.
Checking connectivity... done.

$ cd test/

$ ls
README.md  SUMMARY.md

$ git log --oneline 
07bde6c Cleanup example
6d368db Add _book to gitignore
20779f5 Add explanation in README.md
1b5b1a6 Create chapter-1/ARTICLE1.md
77b1858 Add help message in SUMMARY.md
210e3fe Create chapter-1/README.md
5570112 Create SUMMARY.md
2a8a0c3 Initial commit
```

创建好的书籍默认已经创建了一些内容，但是这些内容是还没有发布.



### 编辑内容

使用 `gitbook init`, `gitbook serve` 来预览，完成后，可以提交修改：

```
$ git commit -asm "init book"
```

### 发布内容

最后，提交到远程 Git 项目：

```
$ git push 
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 362 bytes | 0 bytes/s, done.
Total 3 (delta 1), reused 0 (delta 0)
To https://github.com/dudusky/gitbook.git
   07bde6c..b6a8b3f  master -> master
```

### 阅读书籍

提交到 GitBook.com 后，书籍就自动发布了，用户就可以通过书籍的地址访问了，例如：`https://keliu1.gitbooks.io/my-gitbook/content/`



点击 "READ" 按钮就可以阅读书籍的内容了



https://help.gitbook.com/books/what-are-change-requests.html



![](https://help.gitbook.com/assets/editor-create-cr.png)