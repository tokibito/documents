========================================
標準モジュール
========================================

Pythonには標準で多数のモジュールが同梱されています。あまりに数が多いため全て把握するのは大変ですが、有用なモジュールを押さえておけば開発効率は飛躍的にアップします。

os
========

:document: http://www.python.jp/doc/release/library/os.html

ファイルとディレクトリを扱うモジュールです。色々な機能がありますが、特に使用頻度の高い関数を紹介します。

* os.path - ファイルパスをいじくる


joinでファイルパスを繋げます。
+演算子やフォーマット文字列を使った結合と違い、不正なパスが生成されません。

.. code-block:: pycon

    >>> import os
    >>> path = os.path.join('/home/bucho', 'show.jpg')
    >>> print path
    /home/bucho/show.jpg


    >>> dir = '/home/bucho'
    >>> name = 'show.jpg'
    >>> path = dir + name
    >>> print path
    /home/buchoshow.jpg  # 意図しないパスになってしまう

existsでファイル/ディレクトリの存在チェックを行えます。

.. code-block:: pycon

    >>> os.path.exists(path)
    True

dirnameでディレクトリパスが得られます

.. code-block:: pycon

    >>> os.path.dirname(path)
    '/home/bucho'

splitextでパスを拡張子とそれ以外に分割できます

.. code-block:: pycon

    >>> name, ext = os.path.splitext(path)
    >>> print name
    /home/bucho/show
    >>> print ext
    .jpg

* os.walk - ファイルとディレクトリの一覧を得る

検索対象パスを指定してos.walkを呼び出すと、検索パス, パスに含まれるフォルダ名のリスト, パスに含まれるファイル名のリストの３要素タプルを生成するジェネレータが返ります。
最初に渡した検索パス以下のすべてのファイル/フォルダが再帰的に検索されます。

.. code-block:: pycon

    >>> import os
    >>> for path, folders, files in os.walk('/home/bucho'):
    ...     for file in files:
    ...         print path + file
    ...
    ...
    /home/bucho/daisuki.3gp
    /home/bucho/hagesii.wmv
    /home/bucho/tof.jpg
    /home/bucho/wozozo.bmp
    /home/bucho/.ero/show.jpg
    /home/bucho/.ero/hide/show.jpg

re
====

:document: http://www.python.jp/doc/release/library/re.html

正規表現を扱うモジュールです。

正規表現内ではバックスラッシュが頻出するため、raw文字列（r''）を使って記述するのが良いでしょう。

正規表現にマッチするとMatchObjectが返ります。

.. code-block:: pycon

    >>> import re
    >>> match_obj = re.search(r'(\d+)$', 'aita255')
    >>> print match_obj.group(1)
    255

何度もマッチングを繰り返す場合は、コンパイル済み正規表現オブジェクトを使うことで負荷を軽減することも出来ます。

.. code-block:: pycon

    >>> compiled = re.compile(r'(\d+)$')
    >>> compiled.search(...

pdb
===

:document: http://www.python.jp/doc/release/library/pdb.html

pythonのデバッガです。

set_traceを実行すると、コードの実行を途中で停止し、デバッグ用のプロンプトが表示されます。実際に動作している時のコードの状態を確認できるため、非常に有用です。

.. code-block:: pycon

    >>> import pdb;pdb.set_trace()
    >>> if xxx == yyy:
    ...     zzz = True
    ...

上記のコード例の1行目が実行されると、実行が一旦停止されてpdbのプロンプトが表示されます。

プロンプト上では通常のインタプリタと同じようにコードを実行できるほか、停止させている実行を1行分進める/実行中のコードを表示する/強制終了するなどの操作が行えます。

:n: 実行を1行分だけ進めます。
:c: pdbを終了し、スクリプトの実行を再開します。
:q: スクリプトの実行を強制的に終了します。
:s: 実行しようとしている関数の内部に進みます。

datetime
========

:document: http://www.python.jp/doc/release/library/datetime.html

日付と時刻のデータを扱うモジュールです。

.. code-block:: pycon

    >>> from datetime import datetime
    >>> datetime.now()
    datetime.datetime(2011, 10, 15, 9, 41, 00, 000000)

    >>> gantan = datetime(2012, 1, 1, 0, 0, 0)
    >>> gantan.year
    2012

日付のみを扱うdateもあります。

.. code-block:: pycon

    >>> from datetime import date
    >>> date.today()
    datetime.date(2011, 10, 15)


timedeltaを使うと、日付/時間の加減算ができます。

.. code-block:: pycon

    >>> from datetime import datetime, timedelta
    >>> dt = datetime.now()
    >>> dt
    datetime.datetime(2011, 10, 15, 9, 41, 00, 000000)
    >>> dt + timedelta(days=3)
    datetime.datetime(2011, 10, 18, 9, 41, 00, 000000)


random
======

:document: http://www.python.jp/doc/release/library/random.html

乱数を生成します。

random関数は0〜1の範囲の小数をランダムに返します。

.. code-block:: pycon

    >>> import random
    >>> random.random()
    0.6130030617573102
    >>> random.random()
    0.038878091500788026

randint関数は第一引数**以上**、第二引数**以下**の整数値をランダムに返します。

.. code-block:: pycon

    >>> random.randint(1, 10)
    6
    >>> random.randint(1, 10)
    3
    >>> random.randint(1, 10)
    1
    >>> random.randint(1, 10)
    8
    >>> random.randint(1, 10)
    10

urllib, urllib2
===============

:document: http://www.python.jp/doc/release/library/urllib2.html , http://www.python.jp/doc/release/library/urllib.html

URLを開くモジュールです。2.x系ではurllibとurllib2が混在していますが、urllib2の方が色々と優れているため、こちらを利用するのがよいでしょう。

urllib2.urlopenに対象URLを渡して呼び出すと、コンテンツが格納されたfile-like objectが返ります。

.. code-block:: pycon

    >>> import urllib2
    >>> result = urllib2.urlopen('http://www.beproud.jp/')
    >>> print result.read()  # file-like objectなのでreadで読み出します。
    <!DOCTYPE html>
    <html>
        <head>
            <title>HOME | 株式会社ビープラウド</title>
            <meta http-equiv="Content-Language" content="ja" />
            <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
            <meta name="description" content="株式会社ビープラウド Be PROUD [IT High Technology &amp; Human Centric Company]" />
            ...


urlopenのdata引数にapplication/x-www-form-urlencoded形式の文字列を渡すと、POSTリクエストとなります。

app...endoced形式の文字列は、urllib.urlencode関数で簡単に生成することができます。

.. tip::

    urlencode関数は**urllib**モジュールの関数です。

.. code-block:: pycon

    >>> import urllib, urllib2
    >>> post_data = urllib.urlencode({
            'name': 'spam',
        })
    >>> result = urllib2.urlopen('http://aita.jp/tabetai/', data=post_data)


エラーはHTTPError例外としてraiseされます

.. code-block:: pycon

    >>> result = urllib2.urlopen('http://www.beproud.jp/bucho.ero')
    HTTPError: HTTP Error 404: Not Found

openerオブジェクトを作成し、ハンドラの設定を行うことで様々な形式でのリクエストが可能です。

.. code-block:: pycon

    >>> # ベーシック認証のハンドラを追加します
    >>> basic_auth = urllib2.HTTPBasicAuthHandler("Bucho's secret folder", "http://www.beproud.jp/bucho.ero/", 'bucho', 'show')
    >>> opener = urllib2.build_opener(basic_auth)
    >>> result = opener.open('http://www.beproud.jp/bucho.ero/')

json
====

:document: http://www.python.jp/doc/release/library/json.html


jsonを扱うモジュールです。urllib2との組み合わせで使われることが多いかと思います。

json.loadsにjson文字列を渡すと、Pythonのオブジェクトにマッピングされます。

.. code-block:: pycon

    >>> import json
    >>> aita = json.loads('''{
            "result": {
                "organization": "BeProud inc",
                "age": 24,
                "name": "aita",
                "like": [
                    "onigiri",
                    "hamburger",
                    "gyudon",
                    "oomori"
                ]
            }
        }''')
    >>> aita['result']['like']
    [u'onigiri', u'hamburger', u'gyudon', u'oomori']


json.dumpsにリストや辞書オブジェクトを渡すとjson文字列を返してくれます。

.. code-block:: pycon

    >>> json.dumps({
            'result': {
                'name': 'aita',
                'organization': 'BeProud inc',
                'age': 24,
                'like': ['onigiri', 'hamburger', 'gyudon', 'oomori']
            }
        })
    '{"result": {"organization": "BeProud inc", "age": 24, "name": "aita", "like": ["onigiri", "hamburger", "gyudon", "oomori"]}}'
