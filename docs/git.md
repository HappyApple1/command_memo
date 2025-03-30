---
title: Git
nav_order: 2
layout: default
---

# ブランチ

## ブランチ名変更
``` bash
$ git branch -m <branch-name> 
```

## ブランチ削除
``` bash
$ git branch -d <branch-name>
```

### 強制削除
``` bash
$ git branch -D <branch-name>
```

# リベース

## リベースコマンド

``` bash
$ git rebase -i <commit-ID>

pick <commit-ID1> ヘッダー修正
pick <commit-ID2> ファイル追加
pick <commit-ID3> README修正
```

## コミットの並び替えと削除
`<commit-ID3>` のコミットを消す 

`<commit-ID2>` を先に適用する 

``` bash
pick <commit-ID2> ファイル追加 
pick <commit-ID1> ヘッダー修正
```

## コミットをまとめる

``` bash
pick <commit-ID1> ヘッダー修正 
squash <commit-ID2> ファイル追加 
squash <commit-ID3> README修正
```

## コミットの分割

``` bash
pick <commit-ID1> ヘッダー修正
pick <commit-ID2> ファイル追加
edit <commit-ID3> READMEとindex修正
```
``` bash
$ git reset HEAD^
$ git add README
$ git commit -m 'README修正' $ git add index.html
$ git commit -m 'index.html修正' $ git rebase --continue
```

# スタッシュ

## 作業の一次避難
``` bash
$ git stash
```

## 避難した作業の確認
``` bash
$ git stash list
```

## 最新の作業に復元
``` bash
$ git stash apply
```

### ステージの状況も復元
``` bash
$ git stash apply --index
```

### 特定の作業を復元
``` bash
$ git stash apply <stash-name>
```

## 最新の作業を削除
``` bash
$ git stash drop
```

### 特定の作業を削除
``` bash
$ git stash drop <stash-name>
```

## 全作業を削除
``` bash
$ git stash clear
```

# 参考

* [マニュアル](https://git-scm.com/docs/user-manual.html)