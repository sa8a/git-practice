# Gitコマンド

## コミット

- [【必須】Gitコミットの書き方・作法【prefix/emoji】](https://suwaru.tokyo/%E3%80%90%E5%BF%85%E9%A0%88%E3%80%91git%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88%E3%81%AE%E6%9B%B8%E3%81%8D%E6%96%B9%E3%83%BB%E4%BD%9C%E6%B3%95%E3%80%90prefix-emoji%E3%80%91/)

## プルリクエスト

- [参考：プルリクエストとは？一連の流れとやり方](https://backlog.com/ja/git-tutorial/pull-request/01/)
- [参考：Gitを使ってForkからPull Requestを投げるまで](https://qiita.com/takamii228/items/80c0996a0b5fa39337bd)


## Gitコマンドメモ

[参考：Gitでよく使うコマンド一覧](https://qiita.com/uhooi/items/c26c7c1beb5b36e7418e)

### git version

|コマンド|説明|
|:--|:--|
|`git version`|Gitのバージョンを出力する|

### git clone

|コマンド|説明|
|:--|:--|
|`git clone {リポジトリのURL}`|対象リポジトリのデフォルトブランチをクローンする|
|`git clone --depth {深さ} {リポジトリのURL}`|対象リポジトリのデフォルトブランチを指定したコミット数で切り詰めてクローンする|
|`git clone -b {ブランチ名} {リポジトリのURL}`|対象リポジトリの対象ブランチをクローンする|

`git clone --depth 1 {リポジトリのURL}` で、履歴が多いリポジトリをクローンする時間を短縮できます。

### git remote

|コマンド|説明|
|:--|:--|
|`git remote`|リモートリポジトリの一覧を出力する|
|`git remote add {リモートリポジトリ名} {リポジトリのURL}`|対象リポジトリをローカルのリモートリポジトリに追加する|
|`git remote rename {旧リモートリポジトリ名} {新リモートリポジトリ名}`|ローカルの対象リモートリポジトリをリネームする|
|`git remote remove {リモートリポジトリ名}`|対象リモートリポジトリをローカルから削除する|

### git branch

|コマンド|説明|
|:--|:--|
|`git branch`|ローカルブランチの一覧を出力する（チェックアウト中のブランチに `*` が付く）|
|`git branch -a`|ローカルブランチとリモートブランチの一覧を出力する|
|`git branch {ブランチ名}`|対象ブランチを新規作成する（チェックアウトしない）|
|`git branch -d {ブランチ名}`|対象ブランチを削除する|
|`git branch -d -f {ブランチ名}`|対象ブランチを __強制__ 削除する|
|`git branch -D {ブランチ名}`|対象ブランチを __強制__ 削除する|
|`git branch -m {旧ブランチ名} {新ブランチ名}`|対象ブランチをリネームする|

### git checkout

|コマンド|説明|
|:--|:--|
|`git checkout {ブランチ名}`|対象ブランチに切り替える|
|`git checkout -b {ブランチ名}`|対象ブランチを新規作成し、切り替える|
|`git checkout {ファイルパス}`|ワークツリーにある対象ファイルの変更を取り消す|
|`git checkout .`|ワークツリーにある全ファイルの変更を取り消す|

2.23.0で `git switch` と `git restore` コマンドが追加され、 `git checkout` コマンドを使わなくても済むようになりました。

### git switch

|コマンド|説明|
|:--|:--|
|`git switch {ブランチ名}`|対象ブランチに切り替える|
|`git switch -c {ブランチ名}`|対象ブランチを新規作成し、切り替える|
|`git switch --detach refs/tags/{タグ名}`|対象タグに切り替える|

### git restore

|コマンド|説明|
|:--|:--|
|`git restore {ファイルパス}`|ワークツリーにある対象ファイルの変更を取り消す|
|`git restore .`|ワークツリーにある全ファイルの変更を取り消す|
|`git restore --source {コミットID} {ファイルパス}`|対象ファイルの変更を対象コミットに戻す|

### git diff

|コマンド|説明|
|:--|:--|
|`git diff`| __ワークツリー__ にあるファイルの差分を出力する|
|`git diff --cached`| __インデックス__ にあるファイルの差分を出力する|

### git status

|コマンド|説明|
|:--|:--|
|`git status`|変更したファイルの一覧を出力する|
|`git status -s`|`git status` を短い形式で出力する|
|`git status -s -b`|短い形式でもブランチとトラッキングを出力する|

### git add

|コマンド|説明|
|:--|:--|
|`git add {ファイルパス1} {ファイルパス2}...`|対象ファイルをインデックス（コミット対象）に追加する|
|`git add -A`|変更した全ファイルをインデックスに追加する|
|`git add -p {ファイルパス}`|対象ファイルをハンク単位でインデックスに追加する|

### git reset

|コマンド|説明|
|:--|:--|
|`git reset HEAD {ファイルパス}`|ステージングにある対象ファイルをワークツリーに戻す（ `git add {ファイルパス}` を取り消す）|
|`git reset HEAD`|ステージングにある全ファイルをワークツリーに戻す（ `git add -A` を取り消す）|

### git commit

|コマンド|説明|
|:--|:--|
|`git commit`|指定したエディタでメッセージを書き、インデックスにある全ファイルをコミットする|
|`git commit -m "{メッセージ}"`|メッセージを付け、インデックスにある全ファイルをコミットする|

「指定したエディタ」とは、 `.gitconfig` の `editor` で指定しているエディタのことです。

```ini:.gitconfig
[core]
    editor = nvim
```

### git revert

|コマンド|説明|
|:--|:--|
|`git revert HEAD`|直前のコミットを元に戻すコミットを作成する|
|`git revert {コミットID}`|対象コミットを元に戻すコミットを作成する|

### git push

|コマンド|説明|
|:--|:--|
|`git push origin {ローカルブランチ名}`|対象ローカルブランチを `origin` にプッシュする|
|`git push -d origin {リモートブランチ名}`|対象リモートブランチを `origin` から削除する|
|`git push origin {タグ名}`|対象タグを `origin` にプッシュする|
|`git push -d origin {タグ名}`|対象タグを `origin` から削除する|
|`git push -f`|強制プッシュする|
|`git push --force-with-lease`|強制プッシュする（ブランチのアップストリームが変更されている場合などは拒否する）|

### git fetch

|コマンド|説明|
|:--|:--|
|`git fetch origin`|`origin` から最新の履歴を取得する|
|`git fetch --prune origin`|リモートリポジトリ上に存在しなくなったブランチなどの参照を削除し、 `origin` から最新の履歴を取得する|

### git rebase

|コマンド|説明|
|:--|:--|
|`git rebase origin/{ブランチ名}`|`origin` にある対象ブランチを、チェックアウト中のブランチへリベースする|

### git merge

|コマンド|説明|
|:--|:--|
|`git merge origin/{ブランチ名}`|`origin` にある対象ブランチを、チェックアウト中のブランチへマージする|
|`git merge --squash origin/{ブランチ名}`|`origin` にある対象ブランチのコミットをひとつにまとめ、チェックアウト中のブランチへマージする|

### git cherry-pick

|コマンド|説明|
|:--|:--|
|`git cherry-pick {コミットID}`|対象コミットをチェリーピックする|
|`git cherry-pick {始点の1つ前のコミットID}..{終点のコミットID}`|始点から終点までのコミットをチェリーピックする|
|`git cherry-pick {始点のコミットID}^..{終点のコミットID}`|始点から終点までのコミットをチェリーピックする|
|`git cherry-pick --skip`|現在のコミットをスキップして、残りのシーケンスを続ける|
|`git cherry-pick --quit`|失敗したチェリーピックを取り消す|

### git stash

|コマンド|説明|
|:--|:--|
|`git stash list`|スタッシュの一覧を出力する|
|`git stash show`|スタッシュの変更を出力する|
|`git stash push -m "{メッセージ}"`|メッセージを付け、変更をスタッシュにプッシュする|
|`git stash pop`|スタッシュの変更をワークツリーに戻す（スタッシュから __消える__ ）|
|`git stash apply`|スタッシュの変更をワークツリーに戻す（スタッシュから __消えない__ ）|
|`git stash drop`|スタッシュから変更を削除する|

2020/03/12現在、 `git stash save` は非推奨です。
代わりに `git stash push` を使いましょう。

スタッシュについては、以下の記事が参考になります。
<https://qiita.com/chihiro/items/f373873d5c2dfbd03250>

### git log

|コマンド|説明|
|:--|:--|
|`git log`|ログを出力する|
|`git log --graph --name-status --pretty=format:"%C(red)%h %C(green)%an %C(Cyan)%ad %Creset%s %C(yellow)%d%Creset"`|ぼくのかんがえたさいきょうのぎっとろぐ|

### git blame

|コマンド|説明|
|:--|:--|
|`git blame {ファイルパス}`|対象ファイル全体の各行ごとに、最後に編集したリビジョンと作者を表示する|
|`git blame -L {開始行} {ファイルパス}`|対象ファイルの開始行から末尾までを各行ごとに、最後に編集したリビジョンと作者を表示する|
|`git blame -L ,{終了行} {ファイルパス}`|対象ファイルの先頭から終了行までを各行ごとに、最後に編集したリビジョンと作者を表示する|
|`git blame -L {開始行},{終了行} {ファイルパス}`|対象ファイルの開始行から終了行までを各行ごとに、最後に編集したリビジョンと作者を表示する|

### git show

|コマンド|説明|
|:--|:--|
|`git show {コミットID}`|対象コミットのメッセージとテキストの差分を表示する|

### git tag

|コマンド|説明|
|:--|:--|
|`git tag {タグ名}`|タグを付ける|
|`git tag -d {タグ名}`|タグを削除する|

### git rm

|コマンド|説明|
|:--|:--|
|`git rm {ファイルパス}`|対象ファイルを __削除し__ 、Gitの管理外にする|
|`git rm --cached {ファイルパス}`|対象ファイルを __削除せず__ 、Gitの管理外にする|
|`git rm -r {フォルダパス}`|対象フォルダ以下を全削除し、Gitの管理外にする|
