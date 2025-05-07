---
tags:
  - Reference
  - Python
aliases: 
cssclasses: 
publish: false
---
# venv pip

Python LauncherでグローバルなPythonから `venv` や `pip` を使うときはそれぞれのコマンドの前に `py -x.y -m ` を加えること。

例）`venv .venv` ⇒ `py -3.12 -m venv .venv`

※ `-x.y` はPythonのメジャーおよびマイナーバージョンであり省略可能。省略した場合はデフォルトのPythonが使われる。
# venv

### 仮想環境の作成

```powershell
venv .venv
```

### 仮想環境の初期化

```powershell
venv .venv --clear
```

### 仮想環境へ切り替え

```powershell
PowerShellの場合
.venv\\Scripts\\activation.ps1

コマンドプロンプトの場合
.venv\\Scripts\\activation.bat
```

### 仮想環境の終了

```powershell
deactivate
```

### 仮想環境内のPythonをアップデート（変更）する

```powershell
venv .venv --upgrade 
pyコマンドでvenvを起動したPythonのバージョンになるため、実際は py -3.9 -m venv .venv --upgrade などとする。
```

## pip

[pip](https://pip.pypa.io/en/stable/) はPythonの標準のパッケージ管理システムである。

### pip install

`package-name` を指定して依存関係を満足する最新のバージョンをインストールする。

```powershell
pip install package-name_1 package-name_2 ...
```

`package-name` を指定して依存関係を満足する最新のバージョンにアップデートする。

```powershell
pip install -U package-name_1 package-name_2 ...
```

pip自体を依存関係を満足する最新のバージョンにアップデートする。

```powershell
pip install -U pip
```

```powershell
pip check -U pip
```

`requirements.txt` を参照してパッケージをインストールする。

```powershell
pip install -r requirements.txt
```

### pip freeze

`requirements.txt` を作成する。

```powershell
pip freeze > requirements.txt
```

### pip uninstall

`package-name` を指定してアンインストールする。依存関係にあるおまけのパッケージはアンインストールされないことに注意！

```powershell
pip uninstall package-name_1 package-name_2 ...
```

### pip list

現在の環境にインストールされているパッケージの一覧を表示する。

```powershell
pip list
```

現在の環境にインストールされているパッケージのうち最新ではなくなっているものを表示する。

```powershell
pip list -o
```

現在の環境にインストールされているパッケージのうち最新であるものを表示する。

```powershell
pip list -u
```

### pip show

`package-name` を指定してパッケージの各種情報を表示する。

```powershell
pip show package-name
```

- 確認できるパッケージ情報
  Name: 名前 Version: バージョン Summary: 概要 Home-page: ホームページのURL Author: 作成者 Author-email: 作成者のメール連絡先 License: ライセンス Location: ローカルの保存先 Requires: 必要とするパッケージ Required-by: 必要とされているパッケージ

## Windowsタスクスケジューラーで定時起動させる方法

### venv

```Powershell
@rem 実行中はコマンドプロンプトのウィンドウが表示される。
cd %~dp0
call .venv\\Scripts\\activate.bat
python main.py
```

```vbscript
’ こちらは実行中にコマンドプロンプトのウィンドウは表示されない。
Option Explicit
Dim objFSO: Set objFSO = createObject("Scripting.FileSystemObject")
Dim strRootDir: strRootDir = objFSO.getParentFolderName(WScript.ScriptFullName)

Dim objShell: Set objShell = CreateObject("Wscript.Shell")
objShell.CurrentDirectory = strRootDir
objShell.run ".venv\\Scripts\\activate.bat & python main.py", 0
```
