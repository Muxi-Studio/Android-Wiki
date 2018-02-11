# Git 工作流

## 日常提交

Git 作为优秀的版本控制工具要充分利用起来，在平常的时候要多提交代码，完成一个小的功能点或者做出一个小的改动就要提交一次（这样发现这次改动有问题的话反向提交很方便，也不太容易引入 bug ），像每次更改 gradle 文件的版本号都可以作为一次单独的提交。每次提交之前要用git工具看下自己有没有更改与此次提交无关的模块，可以用 Android Studio 自带的 git 插件查看，也可以用 SourceTree 进行查看，要尽量保证自己提交的每一行代码都是跟此次提交相关的，不要引入其他无关文件以及不要开启自动格式化代码，万一自己的格式化规则和别人的不一样那整个文件就会有变动，review 代码的时候会相当难受= =。

多人合作时每天提交代码难免会冲突，这个时候推荐用 git fetch + git rebase 来追加提交你的改动到别人的提交后面。

## 提交格式

使用格式例如 type:commit summary:module 写 git 的 commit message

举个栗子：

在开发校园通项目时可以写出如下 commit msg

```
ui:更改图书馆首页的 ui:图书馆

bugfix:修复课程表不能滑动的问题:课程表

refactor:重构课程表模块:课程表

version:version to 2.1.7:构建
```

每次发一个版本还要打版本号 tag 并提交上去,像 **git tag v2.1.7** 这样。

## 分支

再来说下开发项目时分支的使用，我们组内部开发主要功能都是在主分支 master 开发，每次直到内测没有问题后会 merge 进 release 分支。当线上版本出现 bug 时可以checkout到 release 分支的对应历史提交开一个hotfix$version的分支进行热修复。当要有新的试验性功能或者大版本要开发时要新开一个分支提交代码。确保其稳定后可 merge 进 master 分支。

如果对 git 基础还不是很熟的话可以看下Tower里的[关于 Git](https://tower.im/projects/a1482d8ab658462eb68a7557cb1ba897/docs/0a72bb62f4de4aa08ffb29ece752f5e2/)
