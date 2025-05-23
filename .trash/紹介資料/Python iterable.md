---
tags:
  - Python
  - Reference
aliases: 
cssclasses: 
publish: false
---
# Python iterable

---

## この資料の目的
`for` 文によって繰り返すことができるオブジェクトのことを総称して、**イテラブル** (iterable) と呼ぶ。

## iterable

メンバを1つずつ返すことができるオブジェクト。イテラブルの例としては、すべてのシーケンス型 (list、 str、tuple など) や dict などの非シーケンス型、ファイルオブジェクト、 __iter__() メソッドや __getitem__() メソッドで定義したクラスのオブジェクトなどがあります。

イテラブルは、for ループやシーケンスが必要な他の多くの場所で使用できます (zip()、map() など)。イテラブル・オブジェクトを組み込み関数 iter() の引数として渡すと、そのオブジェクトのイテレータが返されます。このイテレータは、値の集合を1回通過するだけでよい。イテラブルを使用する場合、通常は自分で iter() を呼び出したり、イテレータ・オブジェクトを処理したりする必要はありません。for文は、ループの間イテレータを保持する一時的な無名変数を作成し、自動的にそれを行います。
