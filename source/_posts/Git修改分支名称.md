---
title: Git分支修改
tags: 
- Linux
---

### Git分支重命名

记录一下 git 在已推送远端和未推送远端的重命名方法。

#### 远端分支重命名

1. 重命名本地分支。

   ```bash
   git branch -m oldName newName
   ```

2. 删除远端分支

   <!--more-->

   ```bash
   git push --delete origin oldName
   ```

3. 上传新命名的本地分支

   ```bash
   git push origin newName
   ```

4. 把修改后的本地分支与远程分支关联

   ```bash
   git branch --set-upstream-to origin/newName
   ```

#### 本地分支重命名

1. 前提：未推送到远端。

   ```bash
   git branch -m oldName newName
   ```

   

