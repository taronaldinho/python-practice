# Python 基礎文法まとめ

## 変数と演算子

### 変数名  

- アルファベットや数字などを使える。
- 記号は、`_`（アンダースコア）だけが使える。`_` 以外の `+` や  ` `（半角スペース）は使えない。
- 数字から始めることは不可。`abc123` という変数名はOK。`123abc` は数字で始まるのでエラーとなる。
- ひらがなや漢字なども使えるが、予期しないエラーの原因になってしまうことがあるため推奨しない。
- 変数名として使用不可能なもの、使用しないほうがいいもの

### 値の代入

```python

# ← の後からその行の終わりまでに存在する全ての文字列は「コメント」として無視される。
# 変数aに対して=で値を代入する。
a = 1  

# print()で変数の値を出力する。
print(a)  # 1  

# このようにカンマ区切りで複数の変数に一度に値を代入することもできる。
# ダブルクォーテーション（またはシングルクォーテーション）で値を囲うと文字列となる。
b, c = 1.2, "C"

print(b, c)  # 1.2 C
```


### 演算子

算術演算子（それぞれ `+=` のように `=` を末尾につけることで累積代入演算子となる）

| 和   | 差   | 積   | 商   | 切捨除算 | 剰余  | 累乗   |
| --- | --- | --- | --- | ---- | --- | ---- |
| `+` | `-` | `*` | `/` | `//` | `%` | `**` |

比較演算子（演算の結果 `bool` を返す）

|より小さい|以下|より大きい|以上|等しい|等しくない|同一のオブジェクトである|同一のオブジェクトではない|
|---|---|---|---|---|---|---|---|
|`<`|`<=`|`>`|`>=`|`==`|`!=`|`is`|`is not`|

集合演算子（演算の結果 `bool` を返す）

| 和集合                 | 差集合 | 積集合 | 対称差 |
| ------------------- | --- | --- | --- |
| <code>&#x7c;</code> | `-` | `&` | `^` |

## 基本的な型

| 型の種類 | 真理値                  | 整数         | 浮動小数点               | 複素数         | ヌルオブジェクト   |
| ---- | -------------------- | ---------- | ------------------- | ----------- | ---------- |
| クラス名 | `bool`               | `int`      | `float`             | `complex`   | `NoneType` |
| 値の例  | `True` or `False` のみ | `-2, 0, 5` | `-1.2, 0.0, 3.1415` | `-2+3j, 1j` | `None` のみ  |
 
| 型の種類 | リスト           | タプル           | 集合            | 辞書                             | 文字列       |
| ---- | ------------- | ------------- | ------------- | ------------------------------ | --------- |
| クラス名 | `list`        | `tuple`       | `set`         | `dict`                         | `str`     |
| 値の例  | `[0, 1, 'a']` | `(0, 1, 'a')` | `{0, 1, 'a'}` | `{'k_0': 'v_1', 'k_1': 'v_1'}` | `'hello'` |
### 文字列  

文字列は `str` 型。  

```python
string = "hello"  

# +で文字列同士を連結する。
print(string + ", world!")  # hello, world!  

# *で文字列を繰り返す。
print(string * 3)　　# hellohellohello  

# f-stringで文字列に変数の値を埋め込む。
print(f"{string}, world!")  # hello, world!
print(f"{string=}")         # string='hello' （str以外でも同様。）
print(f"{some_dict['some_key']}") # some_value -> ダブル/シングルクォーテーションを使い分ける。  

# 大文字/小文字化
name = "Python Beginners"
print(name.lower())  # python beginners
print(name.upper())  # PYTHON BEGINNERS
```

エスケープシーケンス

| タブ   | 改行   | バックスラッシュ | シングルクォーテーション | ダブルクォーテーション |
| ---- | ---- | -------- | ------------ | ----------- |
| `\t` | `\n` | `\\`     | `\'`         | `\"`        |

### リスト

`list` → 複数の変数や値を `,` 区切りで並べ、それらの全体を `[ ]` で囲んだもの。整数のインデックスを使って要素にアクセスする。

```python
numbers = [4, 5, 6, 7]

print(type(numbers))  # <class 'list'># len()は要素数を返す。
print(len(numbers))   # 4

# インデックスで要素にアクセス。先頭は0から始まることに注意。-1で末尾にアクセス。
print(numbers[1])   # 5
print(numbers[-1])  # 7

# スライスで要素にアクセス。
print(numbers[0:2])  # [4, 5]
print(numbers[:2])   # [4, 5]
print(numbers[1:])   # [5, 6, 7]

# 要素の追加。listは異なる型を含むことができる。
numbers.append("百")
print(numbers)  # [4, 5, 6, 7, '百']
```

### リスト内包表記

```python
[e*2 for e in range(5)]

# [0, 2, 4, 6, 8]
```

### タプル

`tuple` → 変更できない `list` のような型。こちらは `( )` で囲う。

### 集合

`set` → 要素の重複がない。要素は順序を持たない。こちらは `{ }` で囲う。

### 辞書

`dict` → キー（key）とそれに対応する値（value）をセットにして格納することができる型。`{key_0: value_0, key_1: value_1, ...}` のように定義する。

```python
scores = {"Math": 90, "Science": 75, "English": 80}

print(scores["Math"])  # 90

# 値の書き換え
scores["English"] = 100
print(scores["English"])  # 100
```

- `dict.keys()`: キーのリストを取得。
- `dict.values()`: 値のリストを取得。
- `dict.items()`: 各要素の `(key, value)` のタプルが並んだリストを取得。

## 制御構文

### 繰り返し

```python
names = ["佐藤", "鈴木", "高橋"]

for i in range(len(names)):
    print(f"{names[i]}さん")

# 佐藤さん
# 鈴木さん
# 高橋さん
```

### 条件分岐

```python
a = 0

if a > 0:
    print("0より大きいです")
elif a == 0:
    print("0です")
else:
    print("0より小さいです")

# 0です
```

### ループ

```python
count = 0

while count <= 10:
    if count % 2 == 0:
        count += 1
        continue       # 以下の処理を行わずループの先頭に戻る。

    # ifブロックに入らなければこちらの処理が実行される。
    print(count)
    count += 1

# 1
# 3
# 5
# 7
# 9
```

## 関数の基本

ひとまとまりの処理のためのコードをまとめて、プログラム全体の色々な箇所から再利用できるように関数にしておくと便利。

Pythonには組み込み（Pythonをインストールすれば最初から使える）関数が用意されている。ここまで出てきた、`print()` や `type()` などは組み込み関数である。

組み込み関数
[https://docs.python.org/ja/3/library/functions.html](https://docs.python.org/ja/3/library/functions.html)

### ユーザー定義関数

独自の処理を定義した、ユーザー定義関数も作成できる。

```python
# 引数として受けたふたつの値を足し合わせて返す関数。
def add(a, b):
    return a + b

add(5, 10)  # 15
```

## 関数についてもう少し詳しく

### 可変長引数

任意の個数の引数を受けることができる関数を定義したいときは、以下のように引数の前にアスタリスク `*` を付けます。こうすると、その関数は渡された1つ以上の引数をタプルとして受け取り、関数内部で処理することができます。

このような引数を **可変長引数** と言います。Pythonでは `*args` とされることが多いですが、`args` の部分は他の名前でも構いません。

```python
# argsに1つ以上の引数をタプルとして受ける。
def print_lines(*args):
    for a in args:
        print(a)

# 引数として与えた可変長個の値を1行ずつ表示することができる。
print_lines("One")
print_lines("One", "Two")
print_lines("One", "Two", "Three", "Four", "Five")
```

### 可変長キーワード引数

任意の個数のキーワード引数を受けることができる関数を定義したいときは、以下のように引数の前にアスタリスクをふたつ `**` 付けます。こうすると、その関数は渡された1つ以上の引数を辞書として受け取り、関数内部で処理することができます。

このような引数を **可変長キーワード引数** と言います。Pythonでは `**kwargs` とされることが多いですが、`kwargs` の部分は他の名前でも構いません。

```python
def print_key_and_values(**kwargs):
    for k, v in kwargs.items():
        print(f"{k}: {v}")

print_key_and_values(height=172, weigit=72)
# height: 172
# weigit: 72
```

### キーワード引数

ここまで紹介した引数は 位置引数 と呼ばれ、`def` で定義した引数の順に従って引数を受け取ります。

それに対して、以下のような **キーワード引数** を使うと関数は引数名とそれに渡す値を `引数名=引数値` の形で受けることができます。 その際、引数は順不同で関数に渡すことができます。また、キーワード引数で関数を呼び出しておいた方が比較的可読性が高くなります。

```python
# 前に定義したadd()に関数を定義したときとは異なる順序でキーワード引数を渡す。
# もちろんadd(a=3, b=5)でもよい。
add(b=5, a=3)
```

### 引数のデフォルト値

引数には、あらかじめ値を与えておくことができます。これは、引数をとる関数を定義する際に、何も引数に値が渡されなかったときにどのような値がその引数に渡されたことにするかをあらかじめ決めておける機能で、その値のことを **デフォルト値** と呼びます。

例えば、上の `hello()` という関数に、`message` という引数をもたせ、そこにデフォルト値を設定しておきます。

この関数は引数に何も与えずに呼び出すと、「Pythonにようこそ!」というメッセージを表示し、引数に別な値が渡されると、その値を表示します。

```python
def hello(message="Pythonにようこそ!"):
    print(message)
```

```python
hello()
```

```python
hello("Welcome to Python!")
```

デフォルト値が与えられていない引数は関数呼び出しの際に必ず何らかの値が渡される必要がありますが、デフォルト値を持つ場合は何も指定しなくても関数を呼び出すことができるようになります。

### 引数の順序

関数を定義する際、位置引数、デフォルト値を持つ引数、可変長引数、可変長キーワード引数が混在する場合は、

`def 関数名(位置引数, デフォルト値を持つ引数, 可変長引数, 可変長キーワード引数)`

の順で指定する必要があります。

### 位置専用引数とキーワード専用引数

関数を定義する際、以下のように `/` and/or `*` を配置すると、`/` の前の引数は必ず位置引数として、`*` の後の引数は必ずキーワード引数として値を渡され方を制限することができます。

```
def f(pos1, pos2, /, pos_or_kwd, *, kwd1, kwd2):
      -----------    ----------     ----------
        |             |                  |
        |        Positional or keyword   |
        |                                - Keyword only
         -- Positional only
```

### 無名関数（ラムダ/lambda）

```python
a = lambda b, c: b + c
a(2, 3)  # -> 5
```

## クラス

```python
class Dog:
    def __init__(self, name):
        self.name = name

    def bark(self, sound):
        print(f"{self.name}> {sound}")

dog = Dog(name="pochi")
print(f"{dog.name = }")   # dog.name = 'pochi'
dog.bark("わおーん")      # pochi> わおーん
```

## モジュールのインポート

```python
# 正規表現を扱うreをインポート。
import re

# 数学関数を扱うmathから各関数をインポート。
from math import cos, sin, tan, pi

# 行列を扱うnumpyにnpという別名を付けてインポート。
import numpy as np
```

## テキストファイルの入出力

### ファイルからの入力（読み込み）

```python
# 開く対象のファイルはこのNotebookファイルと同じディレクトリにある
# samplesフォルダの中にある sample_r.txt というファイル。
# 相対パスで指定する。
# バックスラッシュがエスケープシーケンスとして認識されないよう先頭に "r" を付けてraw文字列として扱う。
file_path_to_read = r".\samples\sample_r.txt"

# ファイルを読み込み（"r"ead）モード、utf-8 のエンコード方式で開く。
file = open(file_path_to_read, mode="r", encoding="utf8")

# 1 行ずつ読んで表示させる。
text_to_read_1 = file.readline()
print(text_to_read_1)

text_to_read_2 = file.readline()
print(text_to_read_2)

text_to_read_3 = file.readline()
print(text_to_read_3)

# open() したファイルは必ず閉じなければならない。
file.close()
```

```python
# withを使えば、開いたファイルはブロックを抜けた時、自動的に閉じられる。
# また開いたファイルのオブジェクトは as で指定した別名で取り扱う。
with open(file_path_to_read, mode="r", encoding="utf8") as f:
# 一度にすべて表示させる。
    print(f.read())

# 開いたファイルはこの時点で閉じられている。
```

### ファイルへの出力（書き込み）

```python
text_to_write_1 = "（1 行目）これはPythonスクリプトから書き込んだ内容です。"
text_to_write_2 = "（2 行目）これは 2 行目の内容です。"
text_to_write_3 = "（3 行目）これは 3 行目の内容です。この行で終わり。"

# 改行文字 \n で各行の文章を連結する。text_to_write = "\n".join([text_to_write_1, text_to_write_2, text_to_write_3])

# 書き込みファイル（実行前には存在しないので新規作成される）のパスを指定。file_path_to_write_0 = r".\samples\sample_w_0.txt"

# ファイルを書き込み（"w"rite）モード、utf-8 のエンコード方式で開く（なければ作成)。with open(file_path_to_write_0, mode="w", encoding="utf8", ) as f:
    f.write(text_to_write)

# 文章を書き込んだファイルをメモ帳などで開いて確認。
```

### ファイルへの追記

```python
text_to_write_4 = "（4 行目）これは 3 行目の後に追記したい内容です。"

with open(file_path_to_write_0, mode="w", encoding="utf8") as f:
    f.write(text_to_write_4)

# これでは前の 3 行は text_to_write_4 の値で上書きされてしまう…# 文章を書き込んだファイルをメモ帳などで開いて確認。
```