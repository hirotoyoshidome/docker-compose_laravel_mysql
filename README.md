# 環境構築方法

## 事前準備
下記のツールをローカルマシン内（HostOS）にインストールしてください。
* Docker
* docker-compose
* Node 10

## 手順
1. リポジトリをclone
2. アプリケーションの.envファイルの設定

```
cp .env.local .env
```
3. フロントエンドのパッケージをインストール

```
npm install
npm run watch
```
4. 下記のコマンドを実行して、ビルド

```
cd docker
cp .env.example .env
docker-compose up -d --build
docker exec my_mysql /bin/bash -c 'mysql -uroot -proot -e "create database app ;"'
docker-compose exec nginx-php-fpm /bin/bash -c 'cd src && composer install && php artisan key:generate && php artisan migrate'
```
5. HostOS側で下記へアクセス
http://127.0.0.1:80/

画面が表示されることを確認する。

## その他
### 各種ツールについて
macosの場合

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install docker
brew cask install docker
brew install docker-compose
brew install nodebrew
mkdir -p ~/.nodebrew/src
nodebrew install-binary v10.0.0
nodebrew use v10.0.0
echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> ~/.bashrc
```
※ .bashrcがない場合は、.bash_profileに読み込ませる設定記載をする

### コマンド
* コンテナに入る

```
docker-compose exec --user=1000 nginx-php-fpm /bin/bash
```
* コンテナを停止する

```
cd docker
docker-compose stop
```
* 個々のコンテナに入る

```
docker exec -it {container id} /bin/bash
```
* ログを確認する

```
cd docker
docker-compose logs
```

* 停止したプロセスを削除する

```
docker rm $(docker ps -q -a)
```

* マイグレーションを再度実行する場合

```
php artisan migrate:refresh
```
