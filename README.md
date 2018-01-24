# bufan_class2
## git基本操作

+ 暂存
```shell
	//在目录文件夹 输入
	git init

```
+ 查看当前状态
```shell
	//如果没有暂存的文件 会被显示为红色
	git status
```

+ 添加到暂存区
```shell
	//将指定文件或者全部文件添加到暂存区
	git add  index.html
	git add  .  
```

+ 添加到仓库
```shell
	//将暂存区的内容添加到仓库
	git commit -m'描述信息'
	
```


## git操作二
+ 忽略文件
```
	1.添加.gitignore文件
	2.在.gitignore中添加需要忽略的文件名称
```
- 验证readme.md是否被git忽略
- 注意 ：已经被git暂存的文件git忽略是失效的，但是也可以处理
- 一般为了方便代码移植，会把不重要的大文件(夹)忽略，比如以来的js库或者图片资源等

```shell
	//先把之前暂存过的缓存删除 .gitignore配置才能生效
	git rm --cached readme.md
	
```
+ 还原文件
```shell
	//还原
	git checkout index.html
```

## git操作三
+ 时光机 回到过去的某个版本
```shell
	//查看之前提交的历史 这个历史是保存到仓库的记录
	git log 

	//历史的样式
	commit bc3e310c526cd949476a11ee2f6e803802c206e6
	Author: dpq <ne@163.com>
	Date:   Tue Jan 23 15:08:48 2018 +0800

    修改了readme.mdd
	
	//操作回去
	git reset --hard bc3e310...

```

## git分支功能
+ master
> 默认情况下 git创建之后都在主分支进行操作
+ 创建分支
```shell
	//dev 名字自己定义
	git branch  dev
```
+ 切换分支
```shell
	//提示switched branch 'xxx'则切换完毕
	git checkout xxx
	// 通过 命令查看是否切换
	git branch
```
+ 合并分支
```shell
	//当其他分支开发完毕后需要回到主分支 合并代码
	git checkout master
	git merge dev
	//合并后需要手动处理 冲突 ，处理完毕后 commit
	
```
+ 删除分支
```shell
	//如果dev分支已经被合并  可以删除 保持代码分支系统清晰
	git branch -d dev
```


##创建共享仓库
+ mkdir foo.git  手动创建xx.git 文件夹
+ 进入文件 执行  git init --bare 此时便创建了一个裸仓 

+ 往裸仓推送保存
```shell
	// 往xx.git共享仓库的主分支 推送保存
	git push xx.git master
```
+ 新的仓库克隆版本
```shell
	// 需要先克隆共享仓库的版本到demo(名字可以自定义)的目录 
	git clone xx.git demo

```

+ 从共享仓库获取公共代码 并手动合并
```shell
	//如果公共代码与本地不同 需要先进行pull 手动合并
	git pull xx.git master

```
