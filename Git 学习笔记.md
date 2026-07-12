



# Git 学习笔记

> 记录一些Git的使用方式以及常用命令，在使用过程中会补充更多高级知识。
>
> 均以Git 官方中文文档为准（https://git-scm.com/book/zh/v2）

## 目录

[Git 的安装](#Git 的安装)

[Git 的配置](#Git 的配置 (只做一次))

[创建 Git 仓库](#创建 Git 仓库)

[Git 的基础使用案例](#Git 的基础使用案例)

[将 Git 与 GitHub 连接](#将 Git 与 GitHub 连接)

[在不同设备上的使用流程](#在不同设备上的使用流程)

......

---

## 	Git 的安装

- ### Windows 系统的安装步骤

  1.  打开 https://git-scm.com/downloads
  2.  下载 Windows 版本
  3.  一路点 **"Next"**，全部默认安装即可
  4.  安装完成后，在桌面**右键**，你会看到两个新选项：
     - `Git GUI Here`（图形界面，不用管）
     - `Git Bash Here`（我们用的，点这个）

---

## Git 的配置 (只做一次)

安装完成后，你需要先告诉 Git 你是谁。

```sh
# 1. 打开终端 (Windows 右键 → `Git Bash Here`)
# 2. 设置你的用户名（随便写，建议用你的 GitHub 用户名）
git config --global user.name "你的名字"
# 3. 设置你的邮箱（跟 GitHub 注册邮箱一致）
git config --global user.email "你的邮箱@example.com"
```

---

## 创建 Git 仓库

假设你要在 `D:\个人文件` 中管理你的笔记

```sh
# 1. 进入你想放文档的目录
cd D:\个人文件
# 2. 创建一个文件夹（作为你的文档仓库）
mkdir 我的笔记
# 3. 进入这个文件夹
cd 我的笔记
# 4. 初始化 Git 仓库（最重要的一步！）
git init
```

**看到输出：** `Initialized empty Git repository in D:/我的笔记/.git/` 代表成功！

---

## Git 的基础使用案例

- ###  查看状态（随时可以用）

  ```sh
  git status
  ```

- ### 把文件加入跟踪（暂存区）

  ```sh
  git add 文件名.文件格式
  ```

​		**小技巧：** *如果你想添加所有文件，可以用* `git add .`*（点号代表当前目录所有文件）*

- ### 提交（保存为一个版本）

  ```sh
  git commit -m "第一次提交：创建文件"
  ```

- ### 查看历史版本

  ```sh
  git log
  #如果需要更简洁的内容，可以
  git log --online
  ```

- ### 回到旧版本

  1. #### 只是想看看旧版本的内容

     ```sh
     # 用 --oneline 查看 commit id
     git log --oneline
     # 回到旧版本看看（只查看，不改）
     # 将 abc1234 替换为上一步查看的 commit id
     git checkout abc1234 -- 文件名.文件格式
     ```

  2. #### 彻底回退到旧版本

     ```sh
     # 回退到上一个版本
     git reset --hard HEAD~1
     ```

     > **! 警告：** `--hard` *会丢掉之后的修改，慎用！*

  3. #### 想撤销刚才的修改（还没提交)

     ```sh
     # 放弃某个文件的修改
     git checkout -- 文件名.文件格式
     ```

---

## 将 Git 与 GitHub 连接

1. ### 创建一个 GitHub 仓库

   ```tex
   Repository name:   我的笔记          ← 仓库名，跟你的本地文件夹名保持一致
   Description:      我的个人笔记       ← 可选，描述一下
   Public / Private:  选 Public          ← 公开（免费），Private 也行
   不要勾选任何东西！❌ README ❌ .gitignore ❌ License
   ```

2. ### 把本地仓库和 GitHub 连接起来

   ```sh
   # 告诉 Git，远程仓库地址是哪里
   git remote add origin https://github.com/你的用户名/我的笔记.git
   ```

   > *这行命令在 GitHub 仓库创建完成后，页面上会显示*

3. ### 把你的文件推送到 GitHub

   ```sh
   # 推送（上传）到 GitHub
   git push -u origin main
   ```

   > *第一次推送需要登陆，会弹出一个窗口，按步骤登陆即可*

4. ### 在 GitHub 上查看你的仓库

   ```tex
   https://github.com/你的用户名/我的笔记
   ```

   （把 `你的用户名` 和 `我的笔记` 换成你自己的）就能查看到了在不同设备上的使用流程

---

## 在不同设备上的使用流程

- ### 只在一台设备上使用 （比如只在家里使用）

  以下是日常使用流程：

  ```sh
  # 第1步：把所有修改加入暂存
  git add .
  # 第2步：提交成一个版本
  git commit -m "更新了xxx笔记"
  # 第3步：推送到 GitHub
  git push
  ```

  
