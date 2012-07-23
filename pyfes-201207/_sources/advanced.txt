関数
=======================

関数定義
----------

関数はdef文で定義します。引数が無くてもかっこは必須です。

.. code-block:: pycon

  >>> def hello():
  ...     print 'Hello World!'
  ...
  >>> def add(a, b):
  ...     return a + b
  ...

デフォルト引数
--------------

Pythonでは引数のデフォルトの値を決められます。該当の引数が与えられない場合にデフォルトの値が関数に渡されます。

.. code-block:: pycon

  >>> def ian(word='black'):
  ...      print '%s ian' % word
  ...
  >>> ian()
  black ian
  >>> ian('white')
  white ian

可変長引数
----------

``*`` からはじまる引数で可変長の引数をリストとして取得できます。

.. code-block:: pycon

  >>> def sum(*args):
  ...     result = 0
  ...     for x in args:
  ...         result += x
  ...     return result
  ...
  >>> sum(1,2,3,4,5,6,7,8,9,10)
  55
  >>> sum(1, 2, 3)
  6

可変長キーワード引数
--------------------

``**`` からはじまる引数で可変長のキーワード引数が辞書として取得できます。

.. code-block:: pycon

  >>> def f(**kwargs):
  ...     return kwargs
  >>> f(a=1, b=2, c=3)
  {'a': 1, 'c': 3, 'b': 2}
  >>> def g(**kwargs):
  ...     for key, value in kwargs.iteritems():
  ...         print key, value
  >>> g(a=1, b=2, c=3)
  a 1
  c 3
  b 2

特殊な引数指定方法
=====================

リストや辞書の各要素を引数として渡すこともできます。

引数が複雑な関数を呼び出すときや、条件によって引数が細かく変化するような場合に有用です。

.. code-block:: pycon

    >>> def func_a(x, y, z):
    ...     print x + y + z
    ...
    >>> args = [1, 3, 5]
    >>> func_a(*args)  # func_a(1, 3, 5)という呼び出しと等価
    9
    >>> def func_b(name="bucho", age=36):
    ...     print name, age
    ...
    >>> kwargs = {'name': "feiz", 'age': 24}
    >>> func_b(**kwargs)  # func_b(name="feiz", age=24)という呼び出しと等価
    feiz 24

クラス
=======================

自分でデータ型を作成したい場合、Pythonではクラスを作ります。

.. code-block:: pycon

  >>> class Person(object):
  ...     def __init__(self, name, words):
  ...         self.name = name
  ...         self.words = words
  ...     def say(self):
  ...         print u'「%s」と%sさん' % (self.name, self.words)
  ...
  >>> feiz = Person('feiz', u'ふぇ')
  >>> feiz.say()
  「ふぇ」とfeizさん
  >>> tokibito = Person('tokibito', u'ぬるぽ')
  >>> tokibito.say()
  「ぬるぽ」とtokibitoさん


モジュール
=======================

``import`` 文でモジュールが読み込めます。

標準モジュールの ``os`` を読み込んでみましょう。

``import os`` とすると ``os`` モジュール内のオブジェクトにアクセスする事ができます。

.. code-block:: pycon

  >>> import os              # グローバルネームスペースにosが追加される
  >>> os.path.join('/usr/', 'home/bucho/')
  '/usr/home/bucho/'

``from os import path`` とすると ``os.path`` を ``path`` として使うことができます。

.. code-block:: pycon

  >>> from os import path    # グローバルネームスペースにpathが追加される
  >>> path.join('/usr/', 'home/bucho/')
  '/usr/home/bucho/'

ファイル
=======================

ファイルの操作は ``ファイルオブジェクト`` を介して行います。

読み込み
--------

open関数にファイルパスを渡し、読み込み用ファイルオブジェクトを作成します。

.. code-block:: pycon

  >>> fin = open("test.txt")
  >>> fin.read()
  'hello world\ngoodbye world'
  >>> fin.close()

読み込み2
----------------

for文で行ごとの取得ができます。

.. code-block:: pycon

  >>> fin = open("test.txt")
  >>> linenum = 0
  >>> for line in fin:
  ...     linenum += 1
  ...     print "%d: %s" % (linenum, line),
  ...
  1: hello world
  2: goodbye world
  >>> fin.close()

書き込み
--------

ファイルに書き込みをするには、open関数の2つめの引数に"w"を渡し、書き込み用のファイルオブジェクトを作成します。

.. code-block:: pycon

  >>> fout = open("test.txt", "w")
  >>> out.write("hello world")
  >>> fout.close()

file-likeオブジェクト
---------------------

fileオブジェクトのように扱えるオブジェクトは、まとめてfile-likeオブジェクト呼ばれています。

StringIO.StringIOなどがよく使われます。


