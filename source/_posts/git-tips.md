---
title: git备忘录
date: 2025-03-18 00:57:25
tags:
  - git
  - cheat_sheet
---

# git使用技巧

## `git commit`
``` shell
git commit --amend # 修改最后一次commit的message
```

## `git reset`
``` shell
git reset --soft HEAD^ # 回退到上一个版本，但是不删除commit
git reset --hard HEAD^ # 回退到上一个版本，并且删除commit
```

## `git push`
``` shell
git push --force # 强制推送
git push --force-with-lease # 推荐使用
```