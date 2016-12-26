# 使用Git本地库

## 初始化版本库

``` shell
git init
```

## 添加文件

``` shell
git add <file>
```

## 提交

``` shell
git commit [ -m "message"]
```

## 放弃添加文件

``` shell
git rm --cached <file>
```

## 查看当前状态

``` shell
git status
```

## 查看修改

``` shell
git diff <file>
```

## 提交更改

``` shell
git add <file>
git commit [ -m "message" ]
```

## 查看历史版本

``` shell
git log
```

## 查看操作历史

``` shell
git reflog
```

## 回退版本

``` shell
git reset --hard <commit id>
```
### commit id
* HEAD	当前版本
* HEAD^ 上一版本
* HEAD^^ 上上一个版本
* HEAD-100 之前100个版本
* *SHA Code* 版本号

## 放弃工作区修改

``` shell
git checkout -- <file>
```

## 放弃缓存区修改

``` shell
git reset HEAD <file>
```

## 从版本库删除文件
``` shell
git rm <file>
```


# 使用远程库

## 克隆远程库

``` shell
git clone <url>
```


## 本地库关联远程库

``` shell
git remove add origin <url>
```

## 本地库推送到远程库

``` shell
git push origin master
```

## 本地库从远程库拉取更新(fetch)并合并(merge)

``` shell
git pull
```

# 分支操作

## 创建分支并切换

``` shell
git checkout -b <branch name>
```  
相当于  
``` shell
git branch <branch name>
git checkout <branch name>
```

## 查看分支

``` shell
git branch
```

## 切换分支

``` shell
git checkout <branch name>
```

## 分支合并

``` shell
git merge <from branch name>
```

## 删除分支

``` shell
git branch -d <branch name>
```





