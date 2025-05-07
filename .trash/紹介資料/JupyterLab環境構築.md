---
tags:
  - Python
  - Jupyter
  - JupyterLab
  - Reference
aliases: 
cssclasses: 
publish: false
---
# JupyterLab環境構築

---

## この資料の目的

## 動作確認できた環境の情報

### Windows環境

- Windows 10 Pro/Home 22H2 64bit
- Python 3.11.5
- pip 23.2.1
- pipenv 2023.4.29 ※
- Node.js 19.6.1

#### ※補足

2023年9月現在、これより新しいバージョンだと、Windows環境でPythonにパスを通さない場合にお世話になる `py` コマンドから、仮想環境を下記のように作成できない。将来的にはこの不具合に対応してくれるようだが…

```Powershell
PS > py -m pipenv --python 3.9
Warning: Python 3.9 was not found on your system...
Neither 'pyenv' nor 'asdf' could be found to install Python.
You can specify specific versions of Python with:
$ pipenv --python path\to\python
```

### JupyterLab起動環境

- Python 
- JupyterLab 
- Jupyter-lsp 
- Jupyterlab-lsp 
- python-lsp-server 
- jupyterlab-git 

### 用途ごとカーネル

- Python（バージョンは任意）
- ipykernel （バージョンは任意）
- その他使いたいパッケージ（任意）

## Node.jsのインストール

[ダウンロード | Node.js](https://nodejs.org/ja/download/)

最新版を入れとけばOKです。

## フォルダ構成

この説明では以下のようなフォルダ構成に、JupyterLabと拡張機能をインストールするための仮想環境と、用途ごとに異なるパッケージをインストールしてJupyterカーネルとして利用するための仮想環境を作成します。

エクスプローラーや `mkdir` コマンドで下記のように `jupyter` とそのサブフォルダである `lab`,  
`kernels` および、`projects` を作成してください。

```
jupyter
   ├── lab             (←ここにJupyterLabの仮想環境を作る/JupyterLabの起動はここから)
   │   
   ├── kernels
   │   ├─ kernel_1     (←ここにJupyterLabのカーネルとして利用する仮想環境を作る)
   │   ├─ kernel_2     (同上)
   │    …
   ├── projects
   │   ├─ project_1     (←ここにJupyterLabの分析プロジェクト-ノートブックやデータを保管する)
   │   ├─ project_2     (同上)
   │    …
   ├── launch_jupyterlab.bat  
```

`launch_jupyter.bat` はJupyterLabを起動するためのバッチファイルで、ショートカットをデスクトップに置いて使っています。内容は以下の通りです。


```batch
cd .\lab
py -m pipenv run jupyter lab --notebook-dir=".."
```

バッチファイルが起動されると、`lab` に作成する仮想環境を使ってJupyterLabを `jupyter` から立ち上げます。

## JupyterLabを起動する環境の作成

### JupyterLabのインストール

`\jupyter\lab` に移動してPythonとJupyterLabをインストールします。  
ここではPythonはバージョン `3.8`、JupyterLabは `3.0.x` を指定します。JupyterLabには基本機能の他にさまざまな拡張機能をインストールすることができます。ここではJupyterLabでLanguage Server Protocolを利用できるようになる拡張機能 `jupyterlab-lsp` をインストールします。※始めにNode.jsをインストールしたのはJupyterLabで各種拡張機能を使用するためです。

```powershell
PS > cd jupyter\lab
PS jupyter\lab> py -m pipenv --python 3.8
PS jupyter\lab> py -m pipenv install jupyterlab jupyterlab-lsp
```


[krassowski/jupyterlab-lsp: Language Server Protocol integration for JupyterLab](https://github.com/krassowski/jupyterlab-lsp)

次に `python-lsp-server` パッケージをインストールします。  
（`[all]` まで入力すること）

```powershell
PS jupyter\lab> py -m pipenv install 'python-lsp-server[all]'
```


あとはお好みで拡張機能をインストールしてください。ここでは `jupyterlab-git` をインストールします。

```powershell
PS jupyter\lab> py -m pipenv install jupyterlab-git
```


一度JupyterLabを起動します。下記コマンドまたは、前述の `launch_jupyterlab.bat` を実行してください。

```powershell
PS jupyter\lab> py -m pipenv run jupyter lab
```

JupyterLabが起動したら拡張機能を `Enable` にして有効化します。

ここまで完了したら、JupyterLabを終了します。  
JupyterLabの終了は、File→Logoutをクリックしてタブを閉じたのち、シェル側で `Ctrl+C` を行ってサーバをシャットダウンしてください。

## カーネルとして利用する仮想環境の作成

用途ごとのカーネルを作成するためのフォルダに移動して仮想環境を作成します。ここで `ipykernel` は必須のパッケージです。

```powershell
PS > cd jupyter\kernels\kernel_1
PS jupyter\kernels\kernel_1> py -m pipenv --python x.x
PS jupyter\kernels\kernel_1> py -m pipenv install ipykernel numpy pandas ...
```

次に作成した仮想環境をJupyterのカーネルとして利用できるように `ipython kernel install` コマンドを実行します。

```powershell
PS jupyter\kernels\kernel_1> py -m pipenv run ipython kernel install --user --name=kernel_name --display-name=display_name
```

コマンドのオプションについては下記の通りです。

- `--user` → 現在Windowsにログインしているユーザのみが利用できるようにするオプション
- `--name` → システムが認識するためのカーネルの名前（任意の名前を指定）
- `--display-name` → ユーザのために表示するためのカーネルの名前（任意の名前を指定）

このあと `\jupyter\lab` に移動してJupyterLabを起動すればカーネルとして選択できるようになっています。

インストール済みのカーネルをシェルから確認する場合は、このフォルダから、

```powershell
PS jupyter\lab> py -m pipenv run jupyter kernelspec list
```

で一覧表示されます。

また、カーネルのアンインストールはこのフォルダから、

```powershell
PS jupyter\lab> py -m pipenv run jupyter kernelspec uninstall kernel_name
```

と実行します。
