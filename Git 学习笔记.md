



# Git 学习笔记

> 记录一些Git的使用方式以及常用命令，在使用过程中会补充更多高级知识。
>
> 均以Git 官方中文文档为准（https://git-scm.com/book/zh/v2）

## 目录

- [Git 的安装](#Git 的安装)
- [Git 的配置](#Git 的配置 (只做一次))
- [创建 Git 仓库](#创建 Git 仓库)
- [Git 的基础使用案例](#Git 的基础使用案例)
- ......

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
