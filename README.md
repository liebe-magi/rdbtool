# rdbtool
Dropboxのファイルを簡単に扱うためのライブラリ。

## インストール

```sh
pip install rdbtool
```

## 事前準備

- [ここ](https://www.dropbox.com/developers)でDropbox側の設定を行う
  - 設定方法は後日解説記事を作成予定

## 使い方

```python
import rdbtool

# クラスの定義
db = rdbtool.RDB('(アクセストークン)', '(プロジェクト名)')

# ファイルのダウンロード (test.txtというファイルをtest1.txtとしてダウンロード)
db.download_file('test1.txt', 'test.txt')

# ファイルのダウンロード (ファイルの競合を防ぐロックをかける、アップロードでロック解除)
db.download_file('test1.txt', 'test.txt', lock=True)
    
# ファイルのアップロード (test1.txtというファイルをtest2.txtとしてアップロード)
db.upload_file('test1.txt', 'test2.txt')

# ファイルのアップロード (test1.txtというファイルをtest.txtとして上書きアップロード)
db.upload_file('test1.txt', 'test.txt', overwrite=False)

# 共有リンクの取得 (test.txtの共有リンクを取得)
link = db.get_shared_link('test.txt'):
```