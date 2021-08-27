---
title: laravel6でCRUD実装
tags: [laravel, php, blade]
style: border
color: secondary
description: laravel6でCURDを実装してみました。
---

今日は、laravelでCRUDを実装してみました。

CRUDって、FWにおいて一番基本ですね。

<https://appdividend.com/2019/09/12/laravel-6-crud-example-laravel-6-tutorial-for-beginners/>

ここを参考して、コントローラーとRestfulなビューを作成してみました。

<https://github.com/watakumo/laravel-parser/tree/curd>

# 環境

- PHP >= 7.3.12
- Mysql >= 5.5.5-10.0.17-MariaDB
- PHPStrom >= 2019.2
- Laravel Installer 2.3.0
- Composer >= 1.9.1

# Laravel6でCRUDをしてみましょう

Routeを見ると、やはりLaravelもRestfulなアーキテクチャスタイルで設計されているようです。

## 出来上がり

{%- capture carousel_images -%}
https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcSF7DNVWKIIVVZUpvRQEGU9SWlya0N7pTQ9lhJW-htQUGvq3wBI
{{site.url}}/assets/img/laravel-new.png
{{site.url}}/assets/img/laravel-list.png
{{site.url}}/assets/img/laravel-edit.png
{%- endcapture -%}

{% include elements/carousel.html %}

## .envにてDB設定を確認

お先にDBの設定確認です。

shift 二連打！（EclipseのQuick Searchみたいな機能ですね。）

→ .env を開きます。

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=
```

MYSQLのShellで **CREATE DATABAE laravel**　を打ってDBを作ります。

##　M：モデルとDBテーブルの作成

コマンドでモデルを作ります。

```ps
php artisan make:model Job -m

```

\app\Job.phpが作成されます。

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Job extends Model
{
    //
}
```

database\migrationにも　**create_job_table.php**が作成されます。
そのファイルからカラムを追加してみましょう。

```php
public function up()
{
    Schema::create('jobs', function (Blueprint $table) {
        $table->bigIncrements('id');
        $talbe->string('title');
        $table->string('language');
        $table->number('team-number');
        $table->string('description');    
        $table->timestamps();
    });
}
```

Tableを作成しましょう
```
# db変更
php artisan migrate
# 取り消し
php artisan migrate:rollback
```

app\Job.phpにマッピング変数を追加します。

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Job extends Model
{
    protected $data = ['title','languange','teeam-number','description'];
}

```

## V：ビューの作成

Laravelは基本、テンプレート文法を提供しているようです。

テンプレート自体はVueJSでのコンポーネントのように動きます。

ただし、VueJSのMVVMのようなフロント側のデータモデルリングは

していないの、普通にMとVをコンポーネントがつなぎます。

だからVueJSでフロントを作るという考え方が自然だったんですね。

今回は、お手本になるbladeを使ってビューを作成してみます。

### layout.blade.php の作成
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Laravel 6 CRUD Example</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap.min.css">
</head>
<body>
<div class="container">
    @yield('content')
</div>
<script src="{{ asset('js/app.js') }}" type="text/js"></script>
</body>
</html>

```

### 登録画面作成

これをextendsした　**create.blade.php** ファイルを作成します。

```html
@extends('layout')

@section('content')
    <style>
        .upper {
            margin-top: 40px;
        }
    </style>
    <div class="card upper">
        <div class="card-header">
            <h1>新規登録</h1>
        </div>
        <div class="card-body">
            @if ($errors->any())
                <div class="alert alert-danger">
                    <ul>
                        @foreach ($errors->all() as $error)
                            <li>{{ $error }}</li>
                        @endforeach
                    </ul>
                </div><br />
            @endif
            <form method="post" action="{{ route('jobs.store') }}">
                <div class="form-group">
                    @csrf
                    <label for="title">タイトル:</label>
                    <input type="text" class="form-control" name="title"/>
                </div>
                <div class="form-group">
                    <label for="language">開発言語:</label>
                    <input type="text" class="form-control" name="language"/>
                </div>
                <div class="form-group">
                    <label for="team-number">人数:</label>
                    <input type="text" class="form-control" name="team-number"/>
                </div>
                <div class="form-group">
                    <label for="description">詳細:</label>
                    <input type="textarea" class="form-control" name="description"/>
                </div>
                <button type="submit" class="btn btn-primary">登録</button>
            </form>
        </div>
    </div>
@endsection

```

### 一覧（index.blade.php）を作成

ここからはGITHUBのリンクで書きます。

<https://github.com/watakumo/laravel-parser/blob/curd/resources/views/index.blade.php>

### 修正画面（edit.blade.php）を作成

<https://github.com/watakumo/laravel-parser/blob/curd/resources/views/edit.blade.php>



## C：コントローラーとルーターの作成

コントローラーを作ります。　--resourceオプションで

各アクションを動く関数が作成できます。

```ps
php artisan make:controller JobController --resource
```

次では　**routes\web.php** からウェブルーターを設定します。

```
<?php

Route::get('/', function () {
    return view('welcome');
});

Route::resource('Jobs','JobController');

```
正しくルーターが作られたのはコマンドで確認できます。

```
php artisan route:list
```


### コントローラーにて、メソッドのOverride

index, create, store, eidt, update, destroyを定義します。

<https://github.com/watakumo/laravel-parser/blob/curd/app/Http/Controllers/JobController.php>


store,updateメソッドには、validationも付けた作成します。
