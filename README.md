This repository is no longer maintained.

このリポジトリはメンテナンスされていません。

# eccube-amazonlinux-postgresql

## 接続（ターミナル）

> *host $* docker-compose up -d  
> *host $* docker-compose exec php bash  

## 接続（VSCode）

* このリポジトリをワークスペースとして開く
* コマンドパレットより *Remote-Containers: Reopen in Container* を実行

## インストール

> *container $* git clone [ECCUBE-REPO-URL] ./  
> *container $* composer install  
> *container $* npm install  
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

# Symfony単独で起動する場合

## Symfony 3.4最新版 インストール（任意・EC CUBEとの共存は不可）

> *container $* composer create-project symfony/framework-standard-edition:^3.4 . --prefer-source

## インストール中の質問は次の通り回答

| 設定                 | 値         |
| -------------------- | ---------- |
| database_host        | database   |
| database_port        | 5432       |
| database_name        | postgres   |
| database_user        | postgres   |
| database_password    | *（空欄）* |
| mailer_transport     | *（空欄）* |
| mailer_host          | mail       |
| mailer_user          | *（空欄）* |
| mailer_password      | *（空欄）* |
| secret               | *（空欄）* |
| *Do you want to ...* | n          |

## doctrineのバージョンををEC CUBE 4と揃える

> *container $* composer require doctrine/doctrine-bundle:^1.9 doctrine/orm:^2.6 --ignore-platform-reqs  --update-with-dependencies

## データベース設定を変更する

```diff
--- a/app/config/config.yml
+++ b/app/config/config.yml
@@ -39,7 +39,7 @@ twig:
 # Doctrine Configuration
 doctrine:
     dbal:
-        driver: pdo_mysql
+        driver: pdo_pgsql
         host: '%database_host%'
         port: '%database_port%'
         dbname: '%database_name%'
```

## URL

Symfony : http://localhost:8000/ （デフォルト設定の場合）  
MailHog : http://localhost:8025/ （デフォルト設定の場合）  
phpPgAdmin : http://localhost:8432/  （デフォルト設定の場合）  
     ユーザー名 : `postgres` / パスワード : *（入力不要）*
