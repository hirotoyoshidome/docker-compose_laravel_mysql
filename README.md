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

### モデルを作成する

```
php artisan make:model {Model-name}
```

### サーバーを起動する

```
php artisan serve
```

### Keyを設定する(必要があるみたい)

```
php artisan key:generate
```

### ルーティング

```
vi routes/web.php
```

### コントローラー

```
vi app/Http/Controllers/XxxController.php
```

## ビュー

```
vi resources/views/xxx.blade.php
```

