# Git 同步使用说明

本文档教你如何在任何一台电脑上管理并同步这个 Houdini 项目到 GitHub。

---

## 一、第一次：克隆（下载）到新电脑

打开终端（或 Git Bash），进入你想放项目的目录，运行：

```bash
git clone https://github.com/Morgana-lgtm/houdini-bridge.git
```

会自动下载整个仓库到当前目录下的 `houdini-bridge` 文件夹。

> 第一次 push 时，Git Credential Manager 会弹浏览器让你登录 GitHub 授权一次，之后就会记住，不用再登。

## 二、配置身份（新电脑第一次用 git 才需要）

```bash
git config --global user.name "Morgana-lgtm"
git config --global user.email "yinfanailiu555@gmail.com"
```

## 三、日常三步：改完同步

在仓库目录 `houdini-bridge` 里：

```bash
git add -A
git commit -m "写清楚这次改了什么"
git push
```

## 四、多电脑协作：先拉再推

如果 GitHub 上的内容比你本地新（比如在别的电脑改过），直接 push 会被拒绝，先拉取合并再推：

```bash
git pull --rebase origin main
git push
```

## 五、注意事项

- `.hip` 是二进制文件，git 无法自动合并。若两台电脑同时改了同一个文件，会产生冲突（conflict），只能二选一保留。
- 因此尽量**同一时间只在一台电脑上改**，改完立刻 `commit + push`。
- 换电脑前先在旧电脑 push，新电脑开始工作前先 `git pull`，保证两边同步。
- 超过 100MB 的大文件（缓存、模拟结果等）不要传，用 `.gitignore` 挡住。

---

**一句话总结：新电脑先 `clone`，改完 `add → commit → push`，开工作业前先 `pull`。**
