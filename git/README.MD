## Git 基本指令介绍

### git branch

- git branch A：创建 A 分支

### git switch

- git switch B
  - 选择 B 分支
- git switch -c B
  - 创建并选择 B 分支

### git checkout

- git checkout C
  - 选择 C 分支
- git checkout -b C
  - 创建并选择 C 分支

> 可见 `git switch` 和 `git checkout` 在分支操作方面的用处完全一样。那么在分支操作上尽量使用 `git switch`
>
> 1. `git switch` 相较于 `git checkout` 语义更明确
> 2. `git checkout` 除了可以操作分支外，它还可以操作文件。即该命令可以重写工作区，是一个比较危险的命令。
