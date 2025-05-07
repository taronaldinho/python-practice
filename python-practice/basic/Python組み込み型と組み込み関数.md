# Python組み込み型と組み込み関数

## この資料の目的

> [組み込み型](https://docs.python.org/ja/3/library/stdtypes.html)

Pythonの組み込み型（built-in types）とは、Pythonに標準で付属している、さまざまなデータを表現するための「型」である。

> [組み込み関数](https://docs.python.org/ja/3/library/functions.html)

また、一連の処理について名前を付け繰り返し呼び出すことのできる組み込み関数もある。

## 基本的なPython組み込み型

### 型とは

コンピュータ内部で `0` または `1` とであらわされたデータを、どのように扱うかを表すもの。
また、Pythonにおいてはクラスとほぼ同義であり、データの属性やふるまい（メソッド）についても定義している。

### 真理値型、数値型、ヌルオブジェクト型

| 型の種類 | 真理値                  | 整数         | 浮動小数点               | 複素数         | ヌルオブジェクト   |
| ---- | -------------------- | ---------- | ------------------- | ----------- | ---------- |
| クラス名 | `bool`               | `int`      | `float`             | `complex`   | `NoneType` |
| 値の例  | `True` or `False` のみ | `-2, 0, 5` | `-1.2, 0.0, 3.1415` | `-2+3j, 1j` | `None` のみ  |
 
### コレクション型

| 型の種類 | 文字列       | リスト           | タプル           | マッピング                                  | 集合            |
| ---- | --------- | ------------- | ------------- | -------------------------------------- | ------------- |
| 型    | `str`     | `list`        | `tuple`       | `dict`                                 | `set`         |
| 値の例  | `'hello'` | `[0, 1, 'a']` | `(0, 1, 'a')` | `{'key_0': 'val_0', 'key_1': 'val_1'}` | `{0, 1, 'a'}` |

![](../../attachments/Pasted%20image%2020250507160011.png)

これ以降では、Pythonのインタプリタを起動しそれぞれの型の特徴を確認する。

## `bool` ブーリアン型（ブール型/真理値型 とも）

`True`（真）または `False`（偽）のどちらか一方を表す。`True` や `False` の先頭は大文字になることに注意。

```PowerShell
>>> a = True
>>> type(a)
<class 'bool'>
>>> b = False
>>> type(b)
<class 'bool'>
>>> a == b
False
>>> a != b
True
>>>
```

上の実行例の補足:

1. `a = True` の行で、`a` という変数に対して真理値型の値である `True` を代入している。
2. `type()` というPython標準の [[Python組み込み関数|組み込み関数]] を使って、`a` の型（クラス）を調べることができる。
3. `==` は左辺と右辺の値が同じかどうかを真理値で返す [[Python演算子|比較演算子]] である。
4. `!=` は左辺と右辺の値が違うかどうかを真理値で返す演算子である。

### 数値型

#### `int` 整数型

`-100` `0` `43` などの整数を表す。
また、`as_integer_ratio()` や `is_integer()` などのメソッドを持つ。

```PowerShell
>>> a = 10
>>> type(a)
<class 'int'>
>>> a.as_integer_ratio()
(10, 1)
>>> a.is_integer()
True
>>>
```

上の実行例の補足:

1. はじめの行の `10` のように変数に代入する値そのものを リテラル と呼ぶ。
2. `a.as_integer_ratio()` という `int` 型の値が持つ **メソッド** を使って、`a` を整数の比で表した結果を得ることができる。
3. `a.is_integer()` というメソッドで、`a` が `int` かどうかを [[#`bool` ブーリアン型（ブール型/真理値型 とも）|True または False の真理値]] で表した結果を得ることができる。

#### `float` 浮動小数点型

`3.14` `-0.135` などの浮動小数点を表す。リテラルは `.25` のように1の位の `0` を省略できる。
`int` と同じようなメソッドを持つ。

```PowerShell
>>> a = 0.5
>>> type(a)
<class 'float'>
>>> a.as_integer_ratio()
(1, 2)
>>> a.is_integer()
False
>>> b = .25
>>> type(b)
<class 'float'>
>>> b
0.25
>>>
```

特殊な `float` 

- `float("nan")`: 非数（Not a Number）を表す
- `float("inf")`: 正負の符号とともに無限大を表す

#### `complex` 複素数型

Python, complex型で複素数を扱う（絶対値、偏角、極座標変換など） | note.nkmk.me
https://note.nkmk.me/python-complex/


```PowerShell
a = -2+3j
>>> type(a)
<class 'complex'>
>>> b = -1j
>>> type(b)
<class 'complex'>
>>> a + b
(-2+2j)
>>>
```

### `NoneType` ヌルオブジェクト型

**何も値がない** ことを表す。
リテラルは `None`（先頭は大文字）であり、`None` 以外の値を持たない。

`None` との比較は `is` を使う。

```PowerShell
>>> a = None
>>> type(a)
<class 'NoneType'>
>>> a is None
True
```

### `str` テキストシーケンス型（文字列型 が一般的）

文字列を表す。
文字列のリテラルには様々な記述方法がある。通常はダブルクォーテーションで囲うことを推奨。

- シングルクォートで囲う: `'"ダブル" クォートを埋め込むことができます'`    
- ダブルクォートで囲う: `"'シングル' クォートを埋め込むことができます"`
- 三重引用符で囲う: `'''三つのシングルクォート'''`, `"""三つのダブルクォート"""`

```PowerShell
>>> a = 'single quotation'
>>> type(a)
<class 'str'>
>>> b = "DOUBLE QUOTATION"
>>> type(b)
<class 'str'>
>>> c = '''three consecutive single quotation'''
>>> type(c)
<class 'str'>
>>> d = """theee consecutive double quotation"""
>>> type(d)
<class 'str'>
>>> a[0]
's'
>>> a[-1]
'n'
>>> b[0:6]
'DOUBLE'
>>> c[0:5]
'three'
```


```PowerShell
>>> a = 'single quotation'
>>> a.upper()
'SINGLE QUOTATION'
>>> b.lower()
'double quotation'
```

### `tuple` タプル型



### `dict` マッピング型（辞書型/ディクショナリ型 などとも）



## 組み込み関数

https://docs.python.org/ja/3/library/functions.html
        - 関数は何かを返す、または操作する。
        - `print()` `type()` `len()`

シングルクォーテーションで囲われた文字列