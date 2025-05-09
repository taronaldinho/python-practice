---
tags:
  - Reference
  - Python
aliases: 
cssclasses: 
publish: false
---
# Python Step by Step Learning


## この資料の目的

> Pythonを使って定型業務の自動化や簡単なデータ分析などができるようになる。

### 前提

- Windows 11（10でもほぼ同じ）
- Visual Studio Code
- Python 3.12以降
    - Pythonは公式から配布されているもの、または、`uv` を使う場合は [Python Standalone Builds](https://gregoryszorc.com/docs/python-build-standalone/) が公開しているものを利用する。
        - Anacondaは使わない（[企業での利用は原則有償](https://legal.anaconda.com/policies/en?name=terms-of-service#terms-of-service:~:text=2.1%20Organizational%20Use.) のため推奨しない。Anacondaを使う前提で説明されている書籍やWeb記事も多いので要注意）。
    - グローバルなPythonのインストール時のオプションは次のようにする。
        - `py.exe` のインストールに管理者権限を **用いない**（Use admin privilieges whien installing py.exe に **チェックを入れない**）。
        - `python.exe` を環境変数 `PATH` に **追加しない**（Add python.exe to PATH に **チェックを入れない**）。
    - 仮想環境の作成・管理には次の方法を用いる。
        - 標準の `venv` `pip`
        - サードパーティー製の `uv`

## はじめの一歩コース

Pythonの最も基礎的な部分を理解し、自分でコードを書いて実行しながら勉強を開始できるレベルになることが目標。

1. [[プログラミング言語Pythonの紹介|Pythonについて知っている。]]
2. [[notes/Python/紹介資料/PythonをWindows PCにインストールする|PythonをローカルのWindows PCにインストールできる。]]
3. [[Pythonの基本的な実行方法|インストールしたPythonを使うことができる。]]
    1. Python対話実行形式で `Hello World!` や簡単な計算ができる。
    2. Pythonスクリプトで `Hello World from Python Script!` できる。
4. [[Python組み込み型|基本的な組み込み型/関数を理解している。]]
    - 組み込み型 — Python 3.12.2 ドキュメント https://docs.python.org/ja/3/library/stdtypes.html
        - それぞれ何を表現しているのか、何ができるのか
        - int float bool 
        - tuple list dict set str
        - [[Pythonスライス|スライス]]
        - [[Python文字列処理|文字列処理]]
    - 組み込み関数 — Python 3.12.2 ドキュメント https://docs.python.org/ja/3/library/functions.html
        - 関数は何かを返す、または操作する。
        - print() type() len() open()
5. [[Python基本演算|基本演算]]、[[Python条件分岐|条件分岐]]、[[Python繰り返し|繰り返し]] ができる。
6. 標準ライブラリを `import` して使う。標準ライブラリのドキュメントを知っている。
    1. Python 標準ライブラリ
    1. time
7. Pythonの情報源
    1. 公式WEBサイト
        1. 標準ライブラリ https://docs.python.org/ja/3/library/index.html
    2. 公式ドキュメント
    3. PyPI
    4. 

関数

1. `pip` コマンドでPyPI（Python Package Index）からサードパーティーライブラリをインストールできる。
2. 仮想環境の概念・必要性を理解している。
3. `venv` コマンドで仮想環境を作成・利用できる。
4. 

## 基礎文法・機能理解コース

Pythonの基礎的な文法と組み込みの標準ツールの使い方を理解し、より

- 基礎文法
    - [[PEP8]]
    - 関数
    - クラス
    - 例外とエラーハンドリング
    - 内包表記
    - lambda式
    - 型アノテーション
- 組み込み型
    - iterator generator range
- 文字列操作
    - f-string
    - エスケープシーケンス
- コレクション操作
- ファイル操作
- 標準ライブラリ
    - time、datetime
    - math、random
    - pathlib
    - os、sys
    - pprint enum statistics itertools 
    - logging
    - smtplib
- venv pip
    - uv
    - anaconda
- サードパーティーライブラリ
    - numpy
    - pandas
    - matplotlib
    - requests beautifulsoup4
    - selenium
    - pytest



## 実用アプリ


- zipファイル解析ツール
    - バイナリデータの扱い方
- Web API
    - httpリクエスト
- 四則計算練習アプリ
    - オブジェクトプログラミング

## 開発環境コース

- Visual Studio Code
- Jupyter/Google Colaboratory


## ここまでクリアしたら…

- openpyxl
- numpy
- pandas
- matplotlib
- requests
- beautifulsoup4
- selenium
