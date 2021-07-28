## Git 基本指令介绍

### git branch

- **git branch dev**
  - 创建 `dev` 分支
- **git branch -f dev \<some-commit>**
  - 那么 `dev` 分支上的代码就会和 `<some-commit>` 一样，并且历史记录也会是一样，即 `dev` 分支指向了 `<some-commit>`
  - **注意：`some-commit` 必须是其他分支的**
- **git branch -d dev**
  - 删除 `dev` 分支

### git switch

- **git switch dev**
  - 选择 `dev` 分支
- **git switch -c dev**
  - 创建并选择 `dev` 分支

### git checkout

- **git checkout dev**
  - 选择 `dev` 分支
- **git checkout -b dev**
  - 创建并选择 `dev` 分支

> 可见 `git switch` 和 `git checkout` 在分支操作方面的用处完全一样。那么在分支操作上尽量使用 `git switch`
>
> 1. `git switch` 相较于 `git checkout` 语义更明确
> 2. `git checkout` 除了可以操作分支外，它还可以操作文件。即该命令可以重写工作区，是一个比较危险的命令

### git merge

- **git merge dev**
  - 将当前所在分支的最后一个 `commit`，与 `dev` 分支的 `HEAD` 所指向的 `commit` 合并，并生成 `next commit`

### git rebase

- **git rebase main dev**
  - 以 `dev` 分支 `HEAD` 为基准，将 `main` 分支上的所有 `commit` 按顺序在 `dev` 分支上 `create commit`
- **git rebase -i \<commit-one> \<commit-three>**
  - 可对 `<commit-one>` 与`<commit-three>` 之间的提交进行排序、合并、删除等

### git reset

- **git reset \<some-commit>**
  - 将 `HEAD` 回退到 `<some-commit>`，中间的所有 `commit` 将不可见（针对本地而言）

### git revert

- **git revert \<some-commit>**
  - 撤销 `<some-commit>`，并生成当前 `HEAD` 的 `next commit`，某种意义上实现回退

### git cherry-pick

- **git cherry-pick \<some-commit> \<some-commit>....**
  - cherry-pick：择 `commit` 挑选
  - 即按顺序，依次 `create commit` 到本分支
  - **注意： `<some-commit>` 必须是其他分支的**

### ~ 操作符

- **git switch dev~**
  - `~` 操作符，即相对引用
  - 上面的命令会将 `dev` 分支的 `HEAD` 指向上一级父提交
  - `~` 后可跟数字，`~2` 即代表指向上两次的父提交

### git commit --amend

- 修改上个 `commit` 所提交的信息

### git pull --rebase

- `git fetch` 与 `git rebase` 的缩写

### git pull 的参数

- **git pull origin main**
  - `fetch` 远程 `main` 分支的 `commit` 到本地，然后 `merge` 给当前所在分支
- **git pull origin main:foo**
  - `fetch` 远程 `main` 分支的 `commit` 到本地，然后 `merge` 给本地的 `foo` 分支上

### git push 的参数

- **git push origin main**
  - 将当前所在分支的所有 `commit`，push 给远程 `main` 分支，在 `main` 分支上依次 `create commit`
- **git push origin foo:main**
  - 将本地 `foo` 分支的所有 `commit`，push 给远程 `main` 分支，在 `main` 分支上依次 `create commit`
