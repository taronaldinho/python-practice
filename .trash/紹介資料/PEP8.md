---
tags:
aliases:
cssclasses:
publish: false
---
# PEP8

PEP8とは、Pythonコードのコーディング規約（推奨される書き方）である。


PEP 8 – Style Guide for Python Code | peps.python.org
https://peps.python.org/pep-0008/

pep8-ja/index.rst at master · mumumu/pep8-ja · GitHub
https://github.com/mumumu/pep8-ja/blob/master/index.rst

> コードは書くよりも読まれることの方が多い
> code is read much more often than it is written.

## 覚えておきたい規約

### インデント・引用符など

#### インデント

1レベルインデントするごとに、スペースを4つ使いましょう。

#### 空行

トップレベルの関数やクラスは、2行ずつ空けて定義するようにしてください。
クラス内部では、1行ずつ空けてメソッドを定義してください。
関連する関数のグループを分けるために、2行以上空けても構いません(ただし控えめに)。 
関数の中では、ロジックの境目を示すために、空行を控えめに使うようにします。
#### 引用符

Python では、単一引用符 `'` で囲まれた文字列と、二重引用符 `"` で囲まれた文字列は同じです。この PEP では、どちらを推奨するかの立場は示しません。どちらを使うかのルールを決めて、守るようにして下さい。単一引用符 や 二重引用符 が文字列に含まれていた場合は、文字列中でバックスラッシュを使うことを避けるため、もう一方の引用符を使うようにしましょう。可読性が向上します。

### 命名規約
#### 関数や変数の名前

関数の名前は小文字のみにすべきです。また、読みやすくするために、必要に応じて単語をアンダースコアで区切るべきです。
変数の名前についても、関数と同じ規約に従います。
- `lowercase`    
- `lower_case_with_underscores`

#### 定数

定数は通常モジュールレベルで定義します。全ての定数は大文字で書き、単語をアンダースコアで区切ります。
- `MAX_OVERFLOW` 
- `TOTAL`

#### クラスの名前

クラスの名前には通常 CapWords 方式を使うべきです。
主に callable として使われる、ドキュメント化されたインターフェイスの場合は、クラスではなく関数向けの命名規約を使っても構いません。
- `CapitalizedWords`

TOP - PythonZen & PEP 8 検定試験
https://pythonzen-pep8-exam.jp/

