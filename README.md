# eccube-amazonlinux-postgresql

## 接続（ターミナル）

> *host $* docker-composer up -d  
> *host $* docker-compose exec php bash  

## 接続（VSCode）

* このリポジトリをワークスペースとして開く
* コマンドパレットより *Remote-Containers: Reopen in Container* を実行

## インストール

> *container $* git clone ECCUBE-REPO-URL **.**  
> *container $* composer install  
> *container $* bin/console eccube:install *# 設定項目は全てデフォルトで問題ない*  

## データベースへの接続

> *container $* psql

## .env

* APP_ENV  
    eccuve / Symfony
* APP_DEBUG  
    eccuve / Symfony
* PORT_WEB_APP  
    EC CUBEの公開ポート
* PORT_PGSQL  
    PostgreSQLの公開ポート
* PORT_WEB_PHPPGADMIN  
    phpPgAdminの公開ポート
* PORT_WEB_MAIL  
    MailHogの公開ポート

## URL

 EC CUBE : http://localhost:8000/ （デフォルト設定の場合）  
 MailHog : http://localhost:8025/ （デフォルト設定の場合）  
 phpPgAdmin : http://localhost:8432/  （デフォルト設定の場合）  
     ユーザー名 : `postgres` / パスワード : *（入力不要）*
