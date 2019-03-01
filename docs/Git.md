# Git
Git commands

## 实用工具

- [SmartGit](http://www.syntevo.com/smartgit/)

- [LearnGitBranching](http://learngitbranching.js.org)

## 实用技巧

### 代码统计

> 命令

- 查看git上个人代码量  

git log --author="username" --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }' -

- 统计每个人的增删行数     

git log --format='%aN' | sort -u | while read name; do echo -en "$name\t"; git log --author="$name" --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }' -; done

- 查看仓库提交者排名前 5    

git log --pretty='%aN' | sort | uniq -c | sort -k1 -n -r | head -n 5

- 贡献者统计    

git log --pretty='%aN' | sort -u | wc -l

- 提交数统计    

git log --oneline | wc -l

> 工具

- [git-fame-rb](https://github.com/oleander/git-fame-rb)  


## 常用Git命令

> 汇总   

- git log  历史记录

- git status  

- git clean -df	  

- git branch -vv  


> **Git配置相关**    

- git config -l   
查看Git当前配置信息

- git config --global -l  
查看Git当前全局配置信息

- 配置  
$ git config --global user.email "you@email.com"    
$ git config --global user.name "Your Name"    
$ git config --global core.editor "nano"     
$ git config --global color.ui true   
$ git config --global core.autocrlf false   配置Git工具不自动转换换行符(Windows下默认会把sh自动转换为crlf)  
$ git config --global core.fileMode false  配置Git工具不自动转换文件权限  

> 代理设置

Git设置代理  
git config --global http.proxy http://name:psd@xx.xx.com:8080  
git config --global https.proxy https://name:psd@xx.xx.com:8080  

Git取消代理  
git config --global --unset http.proxy  
git config --global --unset https.proxy  

git config --global http.sslverify false


- 特定链接不代理设置（路径 C -> 用户 -> 【我的账号】 -> .gitconfig文件）
[http "http://127.0.0.1"]    
  proxy =      


> **删除远程分支A**    

- git push origin --delete A    

- git push origin :A    


> 修改已commit版本

- git add xx
- git commit --amend --no-edit   # "--no-edit": 不编辑, 直接合并到上一个 commit
- git log --oneline    # "--oneline": 每个 commit 内容显示在一行

> **回退**    


- 回到过去

git reset x

git reset --hard HEAD  # 回到 上一次的 commit

git reset --hard id    # 回到 id指定的 commit

- 远程服务器支持SSH前提下    

git reset –mixed   // 此为默认方式，不带任何参数的git reset，就是这种方式，它回退到某个版本，只保留源码，回退commit和stage信息

git reset –soft    // 回退到某个版本，只回退了commit的信息，不会恢复stage（如果还要提交，直接commit即可)

git reset –hard    // 彻底回退到某个版本， 本地的源码也会变为上一个版本的内容

- 远程服务器不支持SSH    

git branch old_master  //新建old_master分支 作为备份，以防万一

git push origin old_master:old_master //将本地的old_master分支　推送到远程的old_master

git reset –hard //本地仓库　彻底回退到某一个版本

git push origin :master // 删除远程的master分支

git push origin master //重新创建远程master分支

- [Reset、Checkout、Revert-的选择](https://github.com/geeeeeeeeek/git-recipes/wiki/5.2--代码回滚：Reset、Checkout、Revert-的选择)

> **冲突解决**

- [kdiff3](http://kdiff3.sourceforge.net/) 

Git 配置

git config --global --add merge.tool kdiff3    
git config --global --add mergetool.kdiff3.path "C:/xx/KDiff3/kdiff3.exe"    
git config --global --add mergetool.kdiff3.trustExitCode false    
 
git config --global --add diff.guitool kdiff3    
git config --global --add difftool.kdiff3.path "C:/xx/KDiff3/kdiff3.exe"    
git config --global --add difftool.kdiff3.trustExitCode false    

- [git-mergetool](https://git-scm.com/docs/git-mergetool)

- [代码合并：Merge、Rebase-的选择](https://github.com/geeeeeeeeek/git-recipes/wiki/5.1-代码合并：Merge、Rebase-的选择)

> **Git中文乱码** 

$ git config --global core.quotepath false  	# 显示 status 编码   
$ git config --global gui.encoding utf-8			# 图形界面编码   
$ git config --global i18n.commit.encoding utf-8	# 提交信息编码   
$ git config --global i18n.logoutputencoding utf-8	# 输出 log 编码   
$ export LESSCHARSET=utf-8   
最后一条命令是因为 git log 默认使用 less 分页，所以需要 bash 对 less 命令进行 utf-8 编码  

> gitgore 添加文件不起作用（文件已进仓,track）

- 指定文件    
git rm --cached .classpath    
git commit -m "update .gitgore"    

- 所有文件      
git rm --cached .     
git add .         
git commit -m "update .gitgore"     


## 实用链接  

- [git-recipes](https://github.com/geeeeeeeeek/git-recipes/wiki)  Good!
- [《Git权威指南》]()
- [《Git Community Book 中文版》](http://gitbook.liuhui998.com/index.html)
- [Git的奇技淫巧](https://github.com/521xueweihan/git-tips)
- [Git Book](https://git-scm.com/book/zh/v1/)
- [gradle 最近更新说明](https://docs.gradle.org/current/release-notes.html)
- [gradle 归档地址](https://services.gradle.org/distributions/)
- [Gradle User Guide 中文版](https://dongchuan.gitbooks.io/gradle-user-guide-/)
- [gradle DSL](https://docs.gradle.org/current/dsl/)





