=======================
制御構造
=======================

インデント
----------

Pythonではインデントに文法としての意味があります。多くの言語における{}にあたる構造を、インデントが揃った部分として表現します。

一般的にはスペース4つでのインデントがよく使われます。

.. code-block:: python

    if x:
        print x
        print "fe"

    if x:
    print x # 文法エラー

if
------------

.. code-block:: pycon

  >>> x = 20
  >>> if x == 20:
  ...     print 'x equals 20!'
  ... elif x > 20:
  ...     print 'x larger than 20!'
  ... else:
  ...     print 'x smaller than 20!'

ifの条件式部分には、カッコはあってもなくても構いません。不要な場合は書かないのがPythonらしい書き方です:)

for
---

Pythonの ``for`` 文はリストやタプルの要素を順番に反復処理します。

.. code-block:: pycon

  >>> for x in range(3):
  ...     print 'x = %d' % x
  ...
  x = 0
  x = 1
  x = 2

``for`` 文に ``else`` 節を付けると、反復が終了した後に実行される処理を書くことができます。

ただしbreakなどでループを途中で抜けた場合、else節は実行されません。

.. code-block:: pycon

  >>> for x in range(3):
  ...     print 'x = %d' % x
  ... else:
  ...      print 'done'
  ...
  x = 0
  x = 1
  x = 2
  done

while
----------

.. code-block:: pycon

  >>> x = 0
  >>> while x < 10:
  ...     print x,
  ...     x += 1
  0 1 2 3 4 5 6 7 8 9

whileにもelse節が記述できます。forとは違って、whileのブロックが一度も実行されなかった場合にのみelse節のコードが実行されます。

.. code-block:: pycon

    >>> while False:
    ...     print 1
    ... else:
    ...     print 2
    2


with
-----

with文は処理の終了後に必ず実行したい処理を纏めて定義することのできる構文です。

ファイルオブジェクトなど、いくつかの組み込みオブジェクトは標準でwithに対応しています。

.. code-block:: python

    with open('xxx.txt') as f:
        print f.read()

本来openしたファイルオブジェクトはcloseメソッドを呼び出して閉じないといけませんが、with文を使えばwithブロックを抜けた時点で自動的にcloseが呼び出されます。

独自にwithでの処理を定義することもできます。標準パッケージのcontextlibを使うと、簡単に記述することができます。

try
-------

``try`` 節の中でエラーが発生した場合の処理を、 ``except`` 節で記述することができます。

.. code-block:: pycon

  >>> try:
  ...     1 / 0  # ゼロ除算エラーが発生するコード
  ... except:
  ...     print "zero devide error"
  
``except`` に処理するエラー型を指定することで、特定のエラー専用の例外処理を書くこともできます。
何も指定しない場合は、あらゆるエラーが処理されます。

  >>> try:
  ...     f()    # 何かの計算をする関数
  ... except NameError:
  ...     print "name error"
  ... except ValueError:
  ...     print "value error"
  ... except ZeroDivisionError:
  ...     print "zero devide error"
  ... except:
  ...     print "other error"

``finally`` 節を記述すると、``try`` 節の中でエラーが発生してもしなくても、必ず実行される処理を書くことができます。

.. code-block:: pycon

  >>> myfile = open('torumemo.txt')
  >>> try:
 ...     ...
 ... finally:
 ...     myfile.close()
