Pythonのインストール
====================

インストールについてはGoogleで検索すればこと足りると思うので、あまり詳しい説明はここではしません。

:入手先: http://www.python.org/download/

Windowsの場合
-------------

1. インストーラを使用してインストールします
2. 環境変数のPathにPythonをインストールしたディレクトリとScriptsディレクトリを追加してください

  XPの場合、[マイコンピュータ]のプロパティの[詳細設定]タブの[環境変数]から設定できます。

MacOSXの場合
------------

OSX10.5以上であれば、Pythonがインストールされています。

それ以前のバージョン、または最新版を利用する場合は、MacPortsでインストールしたりMacPythonをダウンロードしてインストールしてください。

Ubuntuの場合
------------

最初からPythonがインストールされています。

Hello, world!
=============

ターミナル(コマンドプロンプト)を起動して、 ``python`` と入力して実行してみましょう。
Pythonが対話モードで起動します。

``>>>`` という文字列が表示されれば、Pythonがプログラムを実行できる状態になっています。

``Hello, world!`` という文字列を画面に出力する ``print`` 文の命令を入力して実行してみます。

.. code-block:: pycon

  $ python
  >>> print "Hello, world!"
  Hello, world!

表示されましたか？

データ型
========

整数
----

.. code-block:: pycon

   >>> 123
   123

文字列
------

文字列はシングルクォートかダブルクォートで囲みます。

.. code-block:: pycon

   >>> 'abc'
   'abc'
   >>> "efg"
   'efg'

シングルクォートとダブルクォートで意味の違いはありません。

リスト
------

順序をもった値の集合です。異なる型の値でも同じリストに入れることができます。

0から始まる添え字を使ってリスト中の値を取り出すことができます。

.. code-block:: pycon

   >>> [1, 2, 3]
   [1, 2, 3]
   >>> [1, "abc", [1, 2, 3]]
   [1, 'abc', [1, 2, 3]]
   >>> [1, 2, 3][0]
   1
   >>> [1, 2, 3][1]
   2
   >>> [1, 2, 3][2]
   3

辞書
----

添え字に文字列や数値、オブジェクトを使用できる集合です。

.. code-block:: pycon

   >>> {'a': 10, 2: 'cd'}
   {'a': 10, 2: 'cd'}
   >>> {'a': 10, 2: 'cd'}['a']
   10
   >>> {'a': 10, 2: 'cd'}[2]
   'cd'

タプル
------

値を変更できない集合です。リストと同様に添え字で値を取り出せます。

辞書のキーとして使用することができます。

.. code-block:: pycon

   >>> (1, 2, 3)
   (1, 2, 3)
   >>> {(0, 0): 10, (1, 0): 20, (0, 1): 30, (1, 1): 40}
   {(0, 1): 30, (1, 0): 20, (0, 0): 10, (1, 1): 40}

真偽値
------

.. code-block:: pycon

   >>> True
   True
   >>> False
   False

None
----

値がないことを表すときに使います。

.. code-block:: pycon

   >>> None

演算子
======

.. code-block:: pycon

   >>> 1 + 2 + 3
   6
   >>> 1 - 2
   -1
   >>> 2 * 3
   6
   >>> 3 / 2
   1
   >>> 3 / 2.0
   1.5
   >>> 'abc' + 'efg'
   'abcefg'
   >>> 'ab' * 3
   'ababab'
   >>> False or True
   True
   >>> [1, 2, 3] + [4, 5, 6]
   [1, 2, 3, 4, 5, 6]
   >>> 2 * 2 == 4
   True
   >>> 1 < 2 < 3
   True

スライス
========

Pythonではリストに対して範囲を指定して新しいリストとして切り出したりできます。

.. code-block:: pycon

   >>> [1, 2, 3, 4, 5][1:4]
   [2, 3, 4]
   >>> [1, 2, 3, 4, 5][2:]
   [3, 4, 5]
   >>> [1, 2, 3, 4, 5][:3]
   [1, 2, 3]
   >>> [1, 2, 3, 4, 5][:-1]
   [1, 2, 3, 4]
   >>> [1, 2, 3, 4, 5][::2]
   [1, 3, 5]

文字列に対してもスライスは使えます。

.. code-block:: pycon

   >>> 'abcdef'[2:5]
   'cde'
   >>> 'abcdef'[:-2]
   'abcd'

変数
====

データを再利用するために名前を付けて保持しておくことができます。

.. code-block:: pycon

   >>> x = 1
   >>> foo = 'abc'
   >>> print x, foo
   1 abc
   >>> x + 5
   6

関数
====

.. code-block:: pycon

   >>> def add(x, y):
   ...     return x + y
   ...
   >>> add(10, 20)
   30
   >>> func = add
   >>> func(5, 7)
   12
   >>> add
   <function add at 0x00CC0C30>

インデント
==========

Pythonではインデントは、文法として意味があります。関数や制御構造などで複数の命令のまとまりの範囲を示すために使います。

ソースコード中のインデントに問題がある場合、IndentationErrorとなりプログラムは動作しません。

.. code-block:: pycon

   >>> def say():
   ...     print "foo"
   ...   print "bar"
     File "<stdin>", line 3
       print "bar"
                 ^
   IndentationError: unindent does not match any outer indentation level

制御構造
========

条件分岐
--------

.. code-block:: pycon

  >>> a = 10
  >>> if a == 10:
  ...     print 'a is 10.'
  ... elif a > 20:
  ...     print 'a is bigger than 20.'
  ... else:
  ...     print 'other condition.'
  ...
  a is 10.

繰り返し(1)
-----------

.. code-block:: pycon

  >>> range(5)
  [0, 1, 2, 3, 4]
  >>> for i in range(5):
  ...     print i
  ...
  0
  1
  2
  3
  4

繰り返し(2)
-----------

.. code-block:: pycon

  >>> a = 5
  >>> while a > 0:
  ...     print a
  ...     a -= 1
  ...
  5
  4
  3
  2
  1

ソースコードの再利用とモジュール
================================

Pythonではソースコードをファイルに入力して、読み込ませて実行させることができます。

ソースコードのファイル名は英数と ``-`` (ハイフン)、 ``_`` (アンダースコア)などを使用できます。2バイト文字(日本語)などは使えません。

.. note::

  ファイルをモジュールとして扱う場合、ハイフンはソースコード中ではマイナスとして解釈されてしまうため、モジュール名にはハイフンは使わないほうがよいです。

以下のコードを ``test.py`` という名前で保存します。Pythonのソースファイルの拡張子は ``.py`` です。

.. code-block:: python
   :linenos:

   def add(x, y):
       return x + y

   print add(10, 20)
   print add(5, 10)

実行するには、ターミナル(コマンドプロンプト)からPythonを起動するときに、引数でファイルを指定します。

::

   $ python test.py
   30
   15

コメント
--------

ソースコード中に ``# コメント`` のように書くと、``#``から行末までの文字列はコメントとして扱われます。

.. code-block:: python
   :linenos:

   print 1 + 2 + 3  # comment...

モジュール
----------

一つのプログラムを複数のソースファイルで構成することもできます。Pythonでは外部のソースファイル(**モジュール**)に書かれた関数などを読み込んで使用することができます。

.. code-block:: pycon

   >>> import sys
   >>> sys.platform
   'win32'
日本語の扱い
============

Pythonでは日本語の文字列も扱えます。

.. code-block:: python

   >>> print 'こんにちは'
   こんにちは

文字コード
----------

1バイト単位でデータを扱うコンピュータの場合、英数だけなら1バイトですべての文字を表せます。しかし、日本語などの文字の種類が多い言語を扱う場合はそれでは足りません。
日本語は何バイトかのデータ列で文字を表現します。表現の種類は歴史的な事情もあって、いくつも存在します。
最近はUTF-8という文字コードで扱えば大抵問題はないので、この名前を覚えておけばよいでしょう。

.. note::

   Windowsを使用している場合は、CP932(ShiftJIS)という文字コードも扱うことになるので注意してください

Wikipediaなどで文字コードについて詳しく載っているので、興味のある方は調べてみてください。

* `文字コード - Wikipedia`_

.. _`文字コード - Wikipedia`: http://ja.wikipedia.org/wiki/%E6%96%87%E5%AD%97%E3%82%B3%E3%83%BC%E3%83%89

ユニコード(Unicode)
-------------------

文字コードの一種です。Python2.Xでは、文字列はasciiのバイト列かUnicodeで文字列で文字列を扱います。
大きな違いは文字の長さと1文字あたりのと使用バイト数の扱いです。

asciiバイト列では、1文字は1～3バイト程度で表現します。(文字コードによって使用するバイト数や文字表現が変わります)

sample1.py
~~~~~~~~~~

.. code-block:: python
   :linenos:

   # coding: utf-8
   a = '日本語'
   print a
   print len(a)
   print repr(a) # aの内部表現

UTF-8エンコードでファイルを保存してターミナルから実行した結果を示します。

.. code-block:: python

   $ python sample1.py
   日本語
   9
   '\xe6\x97\xa5\xe6\x9c\xac\xe8\xaa\x9e'

.. note::

   Windowsの場合コマンドプロンプトでの文字コードがcp932になるので、この例のコードを実行すると文字化けします。

Unicode文字列では1文字は2バイトで表現します。(例外もあります)

sample2.py
~~~~~~~~~~

.. code-block:: python
   :linenos:

   # coding: utf-8
   a = u'日本語'
   print a
   print len(a)
   print repr(a) # aの内部表現

UTF-8エンコードでファイルを保存してターミナル(コマンドプロンプト)から実行した結果を示します。

.. code-block:: python

   $ python sample2.py
   日本語
   3
   u'\u65e5\u672c\u8a9e'

この例はWindowsでも正常に表示されます。

ターミナルの対話モードで入力する場合と、ソースファイル内での扱いが異なることに注意してください。

ソースコード中に日本語を記述する場合は、ファイルの先頭の行に ``# coding: utf-8`` のようにファイルの文字コードを指定する必要があります。

`ソースコードの文字コード方式 (encoding)`_ も参照してください。

.. _`ソースコードの文字コード方式 (encoding)`: http://www.python.jp/doc/release/tut/node4.html#SECTION004230000000000000000

.. note::

   対話モードでの日本語入力は、はまりやすいポイントなので、慣れるまでは避けておくのが無難かもしれません。

クラス
======

.. code-block:: pycon

   >>> class Person(object):
   ...     def __init__(self, name):
   ...         self.name = name
   ...     def say(self):
   ...         print 'My name is %s.' % self.name
   ...
   >>> p = Person('tokibito')
   >>> p.say()
   My name is tokibito.

ファイルの読み書き
==================

読み込み
--------

.. code-block:: pycon

   >>> f = open('test.txt')
   >>> f.read()
   'Python hack-a-thon\nhello\n'
   >>> f.close()

書き込み
--------

.. code-block:: pycon

   >>> f = open('output.txt', 'w')
   >>> f.write('test')
   >>> f.close()

参考
----

* `ファイルを読み書きする`_

.. _`ファイルを読み書きする`: http://www.python.jp/doc/release/tut/node9.html#SECTION009200000000000000000

サードパーティのモジュール
==========================

Python Package Index (PyPI)
---------------------------

さまざまなサードパーティのモジュールが登録されているページです。

* http://pypi.python.org/pypi

setuptools
----------

Pythonのサードパーティモジュールをインストールするためのツールの一種です。インストールしておくと ``easy_intall`` コマンドが使えます。
 ``easy_install`` コマンドを使うと、PyPIで公開されているモジュールを簡単にインストールすることができます。

* http://pypi.python.org/pypi/setuptools
