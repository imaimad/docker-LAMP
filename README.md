# 作成動機
開発プロジェクトによってはかなり古いミドルウェアを使ってることも多々あるかと思います。  
XAMMP等で古いバージョンのphpをダウンロードしたりするのはかなり面倒だと個人的に思います。  
またバージョン違いによる動作不良や本番環境との環境差分リスクもあるかと思います。  
そこで誰もが欲しいミドルウェアを容易にローカルで構築できるようにしたいと思い作成しました。
# 環境構築手順
1. プロジェクトのルートディレクトリにDockerフォルダとdocker-compose.ymlを配置してください。

2. docker/php/Dockerfileにインストールしたいphpのバージョンを記入
3. docker/mysql/Dockerfileにインストールしたいmysqlのバージョンを記入
4. 【任意】phpmyadminも欲しい場合はdocker-compose.ymlのコメントを外す（26~35行）
5. 【任意】php.iniを編集する必要がある場合は編集する（mbstring,mysql,mysqliは既に有効化済みです）
6.     $ docker-compose -up -d
    でコンテナを起動
7.     $ dcoker ps
    でコンテナが立ち上がっていることを確認
8. mysqlコンテナに対してDBの作成を行う。（クライアントソフト推奨）
9.  DPの洗い替えをする（クライアントソフト推奨）

# 各接続先
* トップページ http://localhost:8000
* phpmyadmin http://localhost:4000
* MySQL 127.0.0.1:13306

# wordpress補足
ルートディレクトリにphp.iniがある場合はそちらが優先されてしまうため、
一時的に削除するか無効にしてください。
config.phpからデータベースの接続を設定してください。

    define('DB_NAME', '作成したDB名');
    /** MySQL データベースのユーザー名 */
    define('DB_USER', 'root');
    /** MySQL データベースのパスワード */
    define('DB_PASSWORD', 'root');
    /** MySQL のホスト名 */
    define('DB_HOST', 'db');