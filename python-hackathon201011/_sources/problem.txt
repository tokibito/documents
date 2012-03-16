課題
====

課題は順番にこなす必要はありません。面白そうだと思った課題にチャレンジしてみてください。

もちろんこれ以外に自分で課題を持っているならば、それをやってみるのも良いでしょう。

socketモジュールを使ってネットワーク通信
----------------------------------------

1. socketモジュールを使って足し算を行うサーバを作成してください。

   telnetコマンドで次のように ``整数+整数`` のように送信すると足し算の結果を返すサーバを作成してください。

   ::
   
      $ telnet localhost 5000
      Trying 127.0.0.1...
      Connected to debian02.
      Escape character is '^]'.
      10+20
      30
      123+456
      579

2. socketモジュールを使って、1.で作成したサーバにデータを送信して、結果を取得して画面に表示してください。

   引数を渡して実行を行うと結果を返してくれるようにしてみてください

   ::

      $ python add.py 10+20
      30

参考ページ
~~~~~~~~~~

* http://www.python.jp/doc/release/lib/module-socket.html
* http://www.python.jp/doc/release/lib/module-sys.html#l2h-5117

sqlite3モジュールを使ってデータベース作成
-----------------------------------------

1. 引数から入力された品名と金額をsqlite3モジュールを使ってデータベースに入力してください

   ::

     $ python inputdb.py ミカン 50
     $ python inputdb.py リンゴ 100

2. 1で作成したデータベースの内容を一覧表示してください

   ::

     $ python listdb.py
     ミカン 50円
     リンゴ 100円

3. 引数から入力された品名と個数で合計金額を表示してください

   ::
   
     $ python calc.py ミカン 3
     ミカンは3個で150円です

参考ページ
~~~~~~~~~~

* http://www.python.jp/doc/release/library/sqlite3.html
* http://www.python.jp/doc/release/library/sys.html

feedparserモジュールでTwitter検索結果のAtomフィードを取得してみる
-----------------------------------------------------------------

1. 対象のAtomフィードは http://search.twitter.com/search.atom?q=%23shibukawa です。これをfeedparserで取得して発言を一覧表示してみてください。

.. note::

   feedparserはサードパーティモジュールなので、インストールを行ってください。

参考ページ
~~~~~~~~~~

* http://www.feedparser.org/
