# practice_laravel

## コマンド集

### プロジェクトを作成する

```
composer create-project laravel/laravel {pj-name} --prefer-dist
```
### 依存ライブラリをインストールする

```
composer install
```
### マイグレーションファイルを作成する

```
php artisan make:migration create_{table-name}_table --create={table-name}
```
※オプションは--createか--tableでテーブル名を指定する

### マイグレーションを実行する

```
php artisan migrate
```

