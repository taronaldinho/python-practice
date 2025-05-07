# PythonをWindows PCにインストールする

## はじめに

この資料では、Pythonのインストーラーを公式ページからダウンロードし、Windows PCにインストールする手順を説明します。

## 最新バージョンのPythonのインストール

1. [Python Releases for Windows | Python.org](https://www.python.org/downloads/windows/) から最新版（Latest）をクリックします。
    ![](../../attachments/Pasted%20image%2020250507113416.png)
2. `Windows installer (64-bit)` をクリックするとインストーラのダウンロードがはじまる（`ダウンロード` フォルダなどに保管される）。
    ![](../../attachments/Pasted%20image%2020250507113650.png)
3. ダウンロードしたインストーラを実行する。
4. `Install Now` をクリックするとインストールがはじまる。
    ※ここで下のふたつのチェックボックスはチェックを入れずに進めることにする。    
    ![](../../attachments/Pasted%20image%2020250507113722.png)
5. インストール作業は完了。右下の `Close` をクリックする。
    お好みで `Disable path length limit` をクリックして（本格的にPython開発をする場合はクリック推奨）、`Close` で終了です。
    ![](../../attachments/Pasted%20image%2020250507113744.png)

## その他のバージョンのPythonのインストール

PCにはバージョンの異なる複数のPythonをインストールすることもできる。

Pythonの `3.12.2` と `3.11.9` というバージョンを取り上げた場合、

- `3`: メジャーバージョン → 非常に大きな変更があった場合（めったに上がらない）
- `12` `11`: マイナーバージョン → 驚きの少ない変更があった場合（最近は概ね1年で `1` ずつ上がる）
- `2` `9`: マイクロバージョン → バグの修正があった場合（最近は概ねひと月で `1` ずつ上がる））

>【参考】Python のバージョン番号の仕組みはどうなっているのですか？
> https://docs.python.org/ja/3/faq/general.html#how-does-the-python-version-numbering-scheme-work

であり、メジャーまたはマイナーバージョンが異なれば複数のPythonをインストールして使い分けることができる。
![](../../attachments/Pasted%20image%2020250507113810.png)

※サードパーティー製のツールを使うとマイクロバージョンまで指定して使い分けることもできる。

最新版以外のPythonインストーラの入手はこちらから。

Download Python | Python.org
https://www.python.org/downloads/

Windows PCにインストールされた複数のPythonを使い分けるために、[Windows の Python ランチャ](https://docs.python.org/ja/3/using/windows.html#launcher)や [[../../Python仮想環境|仮想環境]] を利用する。
