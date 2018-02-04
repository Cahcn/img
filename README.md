我的FMDX记录（pdf版本），具体数据见pdf文档

部分FMDX记录的录音，统一上传至[Google Drive](https://drive.google.com/drive/folders/0B5Btvote7QyZd3FJTEFIUG9nX0k)（原有的坚果云链接保留，但不再更新）

我的个人主页：[https://cahcn.github.io/](https://cahcn.github.io/)


码云提交代码、文件方式：https://git.mydoc.io/?t=154701
```+Markdown
git pull origin master
<这里需要修改/添加文件，否则与原文件相比就没有变动>

git add .
git commit -am "第一次提交"
git push origin master
  ```

---
如何减小仓库体积？
查看存储库中的大文件：
```+Markdown
git rev-list --objects --all | grep -E `git verify-pack -v .git/objects/pack/*.idx | sort -k 3 -n | tail -10 | awk '{print$1}' | sed ':a;N;$!ba;s/\n/|/g'`
  ```

改写历史，去除大文件
```+Markdown
git filter-branch --tree-filter 'rm -f path/to/large/files' --tag-name-filter cat -- --all
git push origin --tags --force
git push origin --all --force
  ```