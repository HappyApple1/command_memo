---
title: Gitコマンド
nav_order: 2
layout: default
---
## 目次<!-- omit from toc -->

- [1. ブランチ操作](#1-ブランチ操作)
  - [1.1. ブランチ名変更](#11-ブランチ名変更)
  - [1.2. ブランチ削除](#12-ブランチ削除)
    - [1.2.1. 強制削除](#121-強制削除)
- [2. 履歴の修正](#2-履歴の修正)
  - [2.1. リベースコマンド](#21-リベースコマンド)
  - [2.2. コミットの並び替えと削除](#22-コミットの並び替えと削除)
  - [2.3. コミットをまとめる](#23-コミットをまとめる)
  - [2.4. コミットの分割](#24-コミットの分割)
- [3. 変更待避](#3-変更待避)
  - [3.1. 作業の一次避難](#31-作業の一次避難)
  - [3.2. 避難した作業の確認](#32-避難した作業の確認)
  - [3.3. 最新の作業に復元](#33-最新の作業に復元)
    - [3.3.1. ステージの状況も復元](#331-ステージの状況も復元)
    - [3.3.2. 特定の作業を復元](#332-特定の作業を復元)
  - [3.4. 最新の作業を削除](#34-最新の作業を削除)
    - [3.4.1. 特定の作業を削除](#341-特定の作業を削除)
  - [3.5. 全作業を削除](#35-全作業を削除)
- [4. 参考](#4-参考)

## 1. ブランチ操作

### 1.1. ブランチ名変更

``` bash
git branch -m <branch-name> 
```

### 1.2. ブランチ削除

``` bash
git branch -d <branch-name>
```

#### 1.2.1. 強制削除

``` bash
git branch -D <branch-name>
```

## 2. 履歴の修正

### 2.1. リベースコマンド

``` bash
$ git rebase -i <commit-ID>
pick <commit-ID1> ヘッダー修正
pick <commit-ID2> ファイル追加
pick <commit-ID3> README修正
```

### 2.2. コミットの並び替えと削除

`<commit-ID3>` のコミットを消す  

`<commit-ID2>` を先に適用する  

``` bash
pick <commit-ID2> ファイル追加 
pick <commit-ID1> ヘッダー修正
```

### 2.3. コミットをまとめる

``` bash
pick <commit-ID1> ヘッダー修正 
squash <commit-ID2> ファイル追加 
squash <commit-ID3> README修正
```

### 2.4. コミットの分割

``` bash
pick <commit-ID1> ヘッダー修正
pick <commit-ID2> ファイル追加
edit <commit-ID3> READMEとindex修正
```

``` bash
git reset HEAD^
git add README
git commit -m 'README修正' $ git add index.html
git commit -m 'index.html修正' $ git rebase --continue
```

## 3. 変更待避

### 3.1. 作業の一次避難

``` bash
git stash
```

### 3.2. 避難した作業の確認

``` bash
git stash list
```

### 3.3. 最新の作業に復元

``` bash
git stash apply
```

#### 3.3.1. ステージの状況も復元

``` bash
git stash apply --index
```

#### 3.3.2. 特定の作業を復元

``` bash
git stash apply <stash-name>
```

### 3.4. 最新の作業を削除

``` bash
git stash drop
```

#### 3.4.1. 特定の作業を削除

``` bash
git stash drop <stash-name>
```

### 3.5. 全作業を削除

``` bash
git stash clear
```

## 4. 参考

- [マニュアル](https://git-scm.com/docs/user-manual.html)
