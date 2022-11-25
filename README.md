# Gitコマンド

## プルリクエスト

[参考：プルリクエストとは？一連の流れとやり方](https://backlog.com/ja/git-tutorial/pull-request/01/)

### git version

|  コマンド  |  説明  |
| ---- | ---- |
|  `% git version`  |  Gitのバージョンを出力  |

### git clone

|  コマンド  |  説明  |
| ---- | ---- |
|  `% git clone {リポジトリのURL}`  |  対象リポジトリのデフォルトブランチをクローン  |
|  `% git clone -b {ブランチ名} {リポジトリのURL}`  |  対象リポジトリの対象ブランチをクローンする  |

## git branch

|  コマンド  |  説明  |
| ---- | ---- |
|  `% git branch`  |  ローカルブランチの一覧を出力  |
|  `% git branch {ブランチ名}`  |   対象ブランチを新規作成（移動はしない）  |
|  `% git branch -d {ブランチ名}`  |  対象ブランチを削除する  |
