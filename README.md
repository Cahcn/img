我的FMDX记录（pdf版本），具体数据见pdf文档。

部分FMDX记录的录音，统一上传至[Google Drive](https://drive.google.com/drive/folders/0B5Btvote7QyZd3FJTEFIUG9nX0k)（原有的坚果云链接保留，但不再更新）

- 我的博客：[https://cahcn.github.io/](https://cahcn.github.io/)
- GitHub仓库：[https://github.com/Cahcn/img](https://github.com/Cahcn/img)
- 备份仓库：[https://gitee.com/bcler/fmdx](https://gitee.com/bcler/fmdx) （不对外公开）

---

1. [提交代码、文件方式](https://git.mydoc.io/?t=154701)
```+Markdown
git pull origin master
<这里需要修改/添加文件，否则与原文件相比就没有变动>

git add .
git commit -am "第一次提交"
git push origin master  //git push --force origin master
```

2. [如何减小仓库体积？](https://git.mydoc.io/?t=83153)
```+Markdown
查看存储库中的大文件
git rev-list --objects --all | grep -E `git verify-pack -v .git/objects/pack/*.idx | sort -k 3 -n | tail -10 | awk '{print$1}' | sed ':a;N;$!ba;s/\n/|/g'`

改写历史，去除大文件
git filter-branch --tree-filter 'rm -f path/to/large/files' --tag-name-filter cat -- --all
git push [分支] --tags --force
git push [分支] --all --force
```

3. [git如何撤销push](https://blog.csdn.net/chenyiyue/article/details/79461624)
```+Markdown
有时候push到了github后，发现刚刚提交的commit有问题，如何撤销操作呢？

首先，在本地回退版本，使用如下命令：
git reset --hard HEAD^
^的个数表示回退几个版本，^^表示回到上上个版本。

然后，强制push: 
git push [分支] HEAD --force
```