# Pythonの基本的な実行方法

## この資料の目的

Windows PCにインストールしたPythonで処理を実行できる。

- 対話方式による逐次実行 ⇒ インタプリタにPythonコードを1行ずつ入力する、対話形式によって実行する。
- Pythonスクリプトの実行 ⇒ 複数行のPythonコードをまとめたスクリプト（`xxxx.py` というファイル）をインタプリタに読み込ませて実行する。

## 前提

[[PythonをWindows PCにインストールする|PythonをWindows PCにインストールする]] の手順に従ってPythonをインストールしているPCを使うこと。

## インストールしたPythonでHello World!

WindowsではPythonとともにインストールされる [Python Launcher](https://docs.python.org/ja/3/using/windows.html#launcher) が適当な（何も指定しなければPCにインストールされている最新の）Pythonを呼び出してくれる。

※別に説明する [[Python仮想環境|仮想環境]] ではPythonの実行方法が少々異なるので注意。

### 対話モード

まず対話モードでの実行方法を説明する。
実務で対話モードを利用する機会は多くないかもしれないが、簡単に機能を確認するのにはちょうどいい（新バージョンのPythonがリリースされた際など）。

#### Pythonインタプリタの起動

Windowsの「ターミナル」アプリ（Windows 10では「PowerShell」）を起動する。

シェルのプロンプト（`> ` ）に続けて `py` と入力しEnterキーを押す。
Python LauncherによってインストールしたPythonが対話モード（interactive mode）で起動する。
`>>> ` とプロンプトが表示され入力待ちとなる。

![[attachments/Pasted image 20241022162007.png]]

#### 処理の命令と実行結果の確認

プロンプト （`>>> `） に続けて `print("Hello World!")` と入力しEnterキーを押す。
入力したコードが実行され次の行に `Hello World!` と表示され、再び入力待ちとなる。

![[attachments/Pasted image 20241022162538.png]]

※ここでは、Python標準の組み込み関数である `print()` を使って文字列を表示させた。

`1+2` のように計算式を入力しEnterキーを押すと、次の行に演算の結果である `3` が表示され、再び入力待ちとなる。

![[attachments/Pasted image 20241028112033.png]]

※Pythonの対話モードでは `print()` を使わなくても、入力された式（数式や変数）を評価した結果が表示される。

Pythonでは四則演算の演算子として、

- 加算: `+`
- 減算: `-` 
- 乗算: `*`
- 除算: `/`

が利用できる。それぞれ試してみること。
（時間があればこちらも [[Python対話モードの練習]]）

#### インタプリタの終了

対話モードのプロンプトに続けて `exit()` または `quit()`（Python 13.0.0以降ならば `exit` `quit` のように括弧がなくてもよい）と入力しEnterキーを押す。
対話モードのPythonが終了し元のシェルのプロンプト `> ` が表示される。

![[attachments/Pasted image 20241028112700.png]]

※インタプリンタの終了は Ctrl + Dキー でも可能。

「ターミナル」アプリ（または「PowerShell」）は右上の x ボタンで閉じる。
### Pythonスクリプトの実行

一連の処理をまとめて記述したファイル（スクリプトファイル）を作成し、Pythonインタプリタに実行させてみる。

#### スクリプトファイルの作成

デスクトップなどで何もないところを右クリックして「新規作成」→「テキスト ドキュメント」と進み、`新しいテキスト ドキュメント.txt` を作成する。
※ファイル名の拡張子を表示させるようにしておくこと。

![[attachments/Pasted image 20241028114158.png]]

![[attachments/Pasted image 20241028114224.png]]

`新しいテキスト ドキュメント.txt` をShiftキーを押しながら右クリックし、「編集」をクリックしてメモ帳等で開く。

![[attachments/Pasted image 20241028114411.png]]

1行目に `print("Hello World from Python Script!")` と入力し、上書き保存する。

![[attachments/Pasted image 20241028114442.png]]

`新しいテキスト ドキュメント.txt` の名前を、`hello_world.py` に変更する。

![[attachments/Pasted image 20241028114553.png]]

#### スクリプトファイルの実行

`hello_world.py` を、`Shift` キーを押しながら右クリックし、「パスのコピー」を行う。

![[attachments/Pasted image 20241028114709.png]]

「ターミナル」アプリ（または「PowerShell」）を起動する。
シェルのプロンプト `> ` に対して、 `py` に続いて半角スペースを入力、コピーしたスクリプトファイルのパスをペーストしEnterキーを押すと、`hello_world.py` に記述した内容が出力される。

![[attachments/Pasted image 20241028115143.png]]

この例では1行のみのコードであったが、このようにしてスクリプトファイルに記述した一連の処理をまとめて実行することができる。
