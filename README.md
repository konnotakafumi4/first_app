Railsと必要なソフトウェアをインストールする

* 必要なソフトウェアのインストールコマンドが書かれたファイル(シェルスクリプト)をダウンロード
* ダウンロードしたシェルスクリプトを実行する
* インストール完了後、ターミナルの実行に必要な設定ファイルを読み込み直す

#### ターミナル
-----------------------------------------------------------------
##### username:~/environment $ wget https://wals.s3.ap-northeast-1.amazonaws.com/curriculum/rails/environment.sh 
-----------------------------------------------------------------
wgetとはコマンドの一種で、指定されたURLのファイルをダウンロードする、という役割を持っています。

続けて、ターミナルに以下のように入力して、実際にソフトウェアをインストールします。
sh eまで打ってからTABキーを押すと、残りの文字は自動で入力されます。

------------------------------------------------
##### username:~/environment $ sh environment.sh
------------------------------------------------
shは、指定したファイルの中身を実行するためのコマンドです。
今回指定したenvironment.shには、Railsと必要なソフトウェアをインストールするためのコマンドが記述されているため、そのコマンドが実行されます。

バージョン確認

---------------------------------------
##### username:~/environment $ rails -v
##### (出力)Rails 6.1.4
##### username:~/environment $ node -v
##### (出力)v16.13.1
##### username:~/environment $ yarn -v
##### (出力)1.22.11
##### username:~/environment $ convert -version
##### (出力)Version: ImageMagick 7.1.0-6 Q16-HDRI x86_64 2021-08-22 https://imagemagick.org
##### (出力)Copyright: (C) 1999-2021 ImageMagick Studio LLC
##### (出力)License: https://imagemagick.org/script/license.php
##### (出力)Features: Cipher DPC HDRI OpenMP(4.5) 
##### (出力)Delegates (built-in): jng jpeg png tiff zlib
---------------------------------------

最後に、sqliteという、データベースに必要なソフトウェアのバージョンを確認していきます。 ここだけ他のソフトウェアと確認する方法が異なり、irbというコマンドを使用していきます。 irbとは、Rubyをターミナル上で実行するためのコマンドで、sqliteのバージョンはRubyの記述を使って確認します。

------------------------------------------
##### username:~/environment $ irb
##### 3.1.2 :001 > require 'sqlite3'
##### (出力) => true 
##### 3.1.2 :002 > SQLite3::SQLITE_VERSION
##### (出力) => "3.36.0" 
##### 3.1.2 :003 > exit
------------------------------------------

アプリケーションを削除するには

---------------------------------------------------
##### username:~/environment $ rm -rf アプリケーション名
---------------------------------------------------

config.hosts << "~.vfs.cloud9.us-east-1.amazonaws.com" という記述は「~.vfs.cloud9.us-east-1.amazonaws.comというホストからしかアクセスできないようにする」という、セキュリティに関する設定です。

-------------------------
##### (省略)
##### :
##### :
#####  config.hosts.clear
##### end
-------------------------
複数のホストからRailsアプリケーションにアクセスすることができる

コントローラの命名規則
コントローラ名は全て複数形かつ全て小文字で書くようにしましょう。

ルーティング記述
HTTPメソッド 'URL' => 'コントローラ#アクション'

「HTTP」は見たことがあると思います。URLの先頭は、「http」から始まっていますね。
この「HTTP（Hypertext Transfer Protocol）」は、通信規約（プロトコル）の1つで、ユーザーが行いたい処理を
サーバーに伝える役割をしています。ウェブブラウザとウェブサーバ間でやり取りするための規則なので、Railsだけでなく、インターネット全体で使われます。

ユーザーが行いたい処理をサーバーに伝えることを、「HTTPリクエスト」といいます。
たとえば、「リンクをクリックしてページを移動したい」、「ブログに投稿したい」などが、HTTPリクエストです。

モデルの命名規則
モデル名は単数系で先頭は英大文字

カラムの追加コマンド
--------------------------------------------------------
##### $ rails g migration Addカラム名Toテーブル名 カラム名:型名
##### $ rails g migration AddNameToLists name:string
##### $ rails db:migrate
--------------------------------------------------------
カラムの削除コマンド
-------------------------------------------------------------
##### $ rails g migration Removeカラム名Fromテーブル名 カラム名:型名
##### $ rails g migration RemoveNameFromLists name:string
##### $ rails db:migrate
-------------------------------------------------------------
