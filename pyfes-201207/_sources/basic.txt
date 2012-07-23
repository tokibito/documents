=======================
基本編
=======================


Hello World!
=======================

ターミナル(コマンドプロンプト)を起動して、 ``python`` と入力して実行すればPythonが対話モードで起動します。

``>>>`` が標準のpythonインタプリタのプロンプトです。 [#]_

.. code-block:: pycon

  $ python
  >>> print "Hello World!"
  Hello World!

printはpython3から式になります。python2.6からは互換性のため、文でも式でも書けるようになっています。

.. code-block:: pycon

    >>> print("hello world")

.. [#] ipythonなど、>>>でないインタプリタもありますが、やっぱりpythonといえば>>>ですね。

スクリプトファイル
============================

スクリプトファイルは、拡張子.pyで作成します。

hello.py::

    # -*- coding: utf-8 -*-

    print "hello world."

先頭のcoding: utf-8という記述は、スクリプトファイルのエンコーディングを指定するものです。スクリプト内で日本語を扱うときは必ず指定するようにしてください。

.. code-block:: pycon

    $ python hello.py
    hello world.

演算
===============

.. code-block:: pycon

  >>> 1 + 2
  3
  >>> 2 * 2
  4

pythonでは整数同士の割り算の結果は整数に丸められてしまうので注意してください。

いずれか一方が小数であれば小数で計算されます。

.. code-block:: pycon

  >>> 5 / 2
  2
  >>> 10 / 3.0
  3.3333333333333333

加減乗除算に加えて、自乗(**)と剰余(%)が利用できます。

.. code-block:: pycon

  >>> 5 % 2
  1
  >>> 2 ** 4
  16

文字列結合は ``+`` です。更に文字列には ``*`` も使えます。

.. code-block:: pycon

  >>> 'ryo' + 'aita'
  'ryoaita'
  >>> 'feiz,' * 10
  'feiz,feiz,feiz,feiz,feiz,feiz,feiz,feiz,feiz,feiz,'

比較演算
============

比較演算子は ``==``, ``!=``, ``<=`` などがあります。結果として真偽値が返されます

.. code-block:: pycon

  >>> 2 * 3 == 6
  True
  >>> 2 != 2
  False

論理演算
============

論理演算は ``and`` ``or`` ``not`` が利用できます。

.. code-block:: pycon

  >>> 1 and 2   # 1が真なので2が結果
  2
  >>> 0 and 1   # 0が偽なので1は評価されない
  0
  >>> 0 or 1    # 0が偽なので1が評価される
  1

変数
=======================

pythonでは変数は代入した時点で自動的に作成されます。事前に宣言しておく必要はありません。

.. code-block:: pycon

  >>> bucho
  NameError
  >>> bucho = 'show'
  >>> bucho
  'show'

コメント
=========================

#の後ろはコメントになります。

.. code-block:: pycon

    >>> # コメント

複数行コメントの構文はありませんが、複数行文字列で代替できます。

.. code-block:: python

    """コメント
    コメント
    コメント
    """

データ型(1)
=======================

整数, 小数
----------------

.. code-block:: pycon

  >>> 1234
  1234
  >>> 3.14
  3.14


真偽値
--------

.. code-block:: pycon

  >>> True
  True
  >>> False
  False

文字列
------

文字列は ``'`` か ``"`` で囲みます。二つに差はありません。

.. code-block:: pycon

  >>> 'Good morning, Feiz!'
  'Good morning, Feiz!'

文字列に改行を含めるには、 改行文字``\n`` を使うか、三連の(ダブル)クオーテーションで囲みます。

.. code-block:: pycon

  >>> print 'Feiz!\nGood Bye!!'
  Feiz!
  Good Bye!!

  >>> print """Azuma
  ... Kenta"""
  Azuma
  Kenta

エスケープシーケンス(``\``)をそのまま表示するには、 ``\\`` とニ連続で書くか、raw文字列を使います。

raw文字列は、クオーテーションの前に``r``をつけて表します。

.. code-block:: pycon

  >>> print 'Feiz!\nFeeeeeeiz!!'  # 何もしない場合改行して表示される
  Feiz!
  Feeeeeeiz!!

  >>> print 'Feiz!\\nFeeeeeiz!!'  # 2連続で書く場合
  Feiz!\nFeeeeeiz!!

  >>> print r'Feiz!\nGood Bye!!' # raw文字列を使う場合
  Feiz!\nGood Bye!!

クォーテーションの前にuをつけるとUnicode文字列になります。

.. code-block:: pycon

    >>> u"あずま"
    u'\u3042\u305a\u307e'


データ型(2)
===========

リスト
------

順序を持った値の集合です。型が混在しても問題ありません。

.. code-block:: pycon

  >>> mylist = [1, 'aita', True]
  >>> mylist
  [1, 'aita', True]

インデックスは0から始まります。

.. code-block:: pycon

  >>> mylist[1]
  'aita'

インデックスに負の整数を指定すると、リストの終端から値が取り出せます。

.. code-block:: pycon

  >>> mylist[-1]
  True

``in`` 演算子を使うと、ある値がリストの中に存在しているか調べられます。

.. code-block:: pycon

  >>> 'aita' in mylist
  True
  >>> 4 in mylist
  False

``range`` 関数を使うと数値のリストが簡単に作れます。

.. code-block:: pycon

    >>> range(5)
    [0, 1, 2, 3, 4]
    >>> range(3, 10, 2)
    [3, 5, 7, 9]

タプル
------

値を変更できない集合です。値を変更できない以外の特性はリストと同様です。

.. code-block:: pycon

  >>> mytuple = (1, 2)
  (1, 2)
  >>> mytuple[0] = 3  # エラー
  TypeError

1要素のタプルを作るときは、後ろにカンマを入れるのを忘れないようにしましょう。

.. code-block:: pycon

  >>> (1)  # ただの「1」になってしまう
  1
  >>> (1,)
  (1, )

スライス
----------

リストやタプルや文字列の特定の範囲を切り出すことができます。

.. code-block:: pycon

  >>> [1,2,3,4,5][:3]  # 先頭から添字3の一つ前まで
  [1, 2, 3]
  >>> 'Azuma Kenta'[3:]  # 添字3から末尾まで
  'ma Kenta'
  >>> [1,2,3,4,5,6,7,8,9,10][1:-1:2]  # 3つ目を指定するとN個飛びで値を取り出せます。
  [2, 4, 6, 8,]


データ型(3)
===========

辞書
----

添え字に文字列や数値、オブジェクトを使用できる集合です。

.. code-block:: pycon

  >>> {'a': 10, 'b': 20}
   {'a': 10, 'b': 20}
  >>> {'a': 10, 'b': 20}['a']
  10
  >>> {'a': 10, 'b': 20}['b']
  20
  >>> {1: 10, 2: 20}[1]
  >>> 20


None
----

Noneは何もないことを表すのに使われます。

.. code-block:: pycon

  >>> None

フォーマット文字列
========================

Cのprintfのように、文字列に外から値を入れ込むことができます。

値を入れ込みたい場所に、値の型に応じたフォーマット文字列を入れておきます

.. code-block:: pycon

  >>> fmt_string = 'feiz is %d years old.'  # 年齢を入れる部分を%dに置き換えている

値を入れるには、 ``%`` 演算子を使います。

.. code-block:: pycon

  >>> print fmt_string % 24
  feiz is 24 years old.

複数の値を入れる場合は、リストやタプルにします。

.. code-block:: pycon

  >>> '%s is %d years old' % ('aita', 24,)
  'aita is 24 years old'

また、リストやタプルの代わりに辞書を使うことも出来ます。渡した辞書のキーに対応する部分に値が入ります。

.. code-block:: pycon

  >>> '%(name)s told me to install %(product)s' % {'name': "bucho", 'product': "bumblebee",}
  'bucho told me to install bumblebee'
