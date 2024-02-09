# git運用方針
gitの運用方針を整理

## ブランチ管理

| branch | 用途 | 作業者 |
| ---- | ---- | ---- |
| main | 本番リリース用ブランチ<br>直接編集不可、developからのマージのみ許可 | ライブラリ管理者 |
| ita, itb, st, etc... | 検証環境用ブランチ<br>developブランチを親として作成、環境依存のあるファイルは直接編集して管理する。 | ライブラリ管理者 |
| develop | 開発ベースブランチ | ライブラリ管理者 |
| feature | 個人開発ブランチ<br>developブランチへマージしたfeatureブランチはリモートブランチから削除すること | 開発者 |


![gitflow](gitflow.png)

## リポジトリ設定(settings)

| 項目 | |  設定値 | 概要 |
| ---- | ---- | ---- | ---- |
| Pull Requests | | |
| Allow merge commits | | 有効 | |
|^ | message | Default Message | |


### デフォルトブランチ
`develop`

### 

## ブランチ運用

### 個人開発ブランチ

 - 命名規則

    プロジェクトで決めの問題だが、以下サンプル
    ```
    feature/{yyyyMM}/kondo
    ```
 
 - developからブランチ作成

    ```
    git checkout -b feature/202401/kondo origin/develop
    ```

 - コミットメッセージルール

    ここ要検討


### 検証環境用ブランチ

1. developからブランチ作成

    例）リモートのdecelopブランチからitbブランチを作成してリモートに登録
    ```
    git checkout -b itb origin/develop
    git push -u origin itb
    ```
    
1. 環境依存のファイルを更新、push

    IDE等で更新、commit、push

    ![update](update.png)

1. developの最新を取り込む

    ```
    git pull origin develop
    ```
    ※環境依存ファイルに変更がある場合は競合(conflict)が発生するので解消する。
    
    環境依存はローカル優先で、それ以外はdevelopの変更を取り込む

    これもIDE等で更新、commit、push
    
    ![conflict](conflict.png)



## 参考
 - [複数人開発の際にはGitのワークフロー、GitFlowとGitHub Flowを導入すると便利です](https://qiita.com/yousan/items/f0801437644527b00342)
 - [Git コンフリクト解消手順](https://qiita.com/crarrry/items/c5964512e21e383b73da)
 - [【Git】コンフリクト(conflict)が発生しても大丈夫な対処法まとめ](https://qiita.com/shizen-shin/items/391aac7b9febaf11bde6)