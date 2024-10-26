# Git

## 配置

```bash
git config --global user.name "Harvey"
git config --global user.email "phdharvey@gmail.com"
ssh-keygen -t rsa -C "phdharvey@gmail.com"

git config --global user.name "Honbo"
git config --global user.email "hehongbo918@gmail.com"
ssh-keygen -t rsa -C "hehongbo918@gmail.com"
```

## 操作

```bash
git init

git add <files>
    git rm <files>
    git mv -f <old> <new> #更改文件夹名称

git commit -m " 提交的信息，将显示在仓库的更改页面 "
     git reset --hard HEAD^    #返回上一个版本
    git reset --hard   # git clone .git <empty_dir_name> 
    git reset --hard HEAD^^   #上上个
    git reset --hard HEAD~100 #100个版本之前

git branch -m <老分支名> <新分支名>
    git branch -m master main

git remote add origin <仓库地址>

git push -u origin <分支名>
    git push -u origin main

# 用 main push可能出现冲突错误，建议先master push后再更改名字为main
# 或者 : git pull --rebase origin main
# 如果推不上去 : git pull --allow-unrelated-histories origin master
```

```bash
git log  # 查看commit历史

git branch == git branch -l  # local ： 查看所有本地分支
git branch -r    # remote
git branch -a    # all
git branch -v       # 查看最后一次提交
git branch --merged    # 查看已合并的
git branch --no-merged # ...
git branch -M <> # 改变本地默认分支
git branch -D <> # 删除
```

## 问题

```bash
#kex_exchange_identification: Connection closed by remote hostConnection closed by ::1 port 22

VPN造成的问题, 解决办法:
1:
关掉vpn # 有时候到这里就可以了
删除known_hosts和known_hosts.old, 再下载(选择yes)

2:
clash -> General -> Port ==> 改成 22 或者 1081 
可能刚改完并不立即生效, 等一下或者试几次就好了
```
