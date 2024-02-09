# git運用方針
gitの運用方針を整理

## ブランチ管理

|  branch  |  用途  |
| ---- | ---- |
| main | 本番リリース用ブランチ<br>直接編集不可、developからのマージのみ許可 |
| ita, itb, st | 検証環境用ブランチ<br>developブランチを親として作成、環境依存のあるファイルは直接編集して管理する。 |
| develop | 開発ベースブランチ |
| feature | 個人開発ブランチ<br>developブランチへマージしたfeatureブランチはリモートブランチから削除すること |


![gitflow](gitflow.png)

