---
title: laravel6でVUEJS実装1
tags: [laravel, Vue, Node, NPM]
style: border
color: secondary
description: laravel6でVUEJS実装してみました。
---

今回は、前日作ったCURDにVUEをつけてみます。

自己学習中のVueは、Vuexのことろを見ている最中なので、

今日はVueを使う環境のところまで行いました。

<https://github.com/watakumo/laravel-parser/tree/curd>

上記のブランチをmergeして下記の新しいブランチを作成しました。

<https://github.com/watakumo/laravel-parser/tree/withVUE>

# 環境

- PHP >= 7.3.12
- Mysql >= 8.0.18
- PHPStrom >= 2019.2
- Laravel Installer 2.3.0
- Composer >= 1.9.1

# なぜVUEとlaravelなのか？

そうですね。laravelはテンプレートを支援しているので、

フロントのモジュール化もしやすいのに、なぜフロントにもFWをつけるんですかね。

<https://towardsdatascience.com/laravel-and-vue-c30770f1e88>

Vueがいいから??ですかね。

サーバとフロントエンド開発に分けて開発ができることも理由になりそうです。

MVVMパターンでSPAを実装するためにはやはりフロントエンジニアが必要ですね。

# VUEのインストール

ここを参考して実装してみました。

<https://laravel.com/docs/6.x/frontend>


```
# laravel/ui 設置
composer require laravel/ui --dev
npm install
npm vue
```

laravel/uiはartisanコマンドでlaravelプロジェクトでも

簡単にフロントのscaffoldingをできるようにするパッケージです。

scaffolding はMVCなどの開発パターンに合わせて、フレームを指定することを指します。

単純にフォルダやファイルの位置を決めることだと理解しても構わないです。

```
// Generate basic scaffolding...
php artisan ui bootstrap
php artisan ui vue
php artisan ui react

// Generate login / registration scaffolding...
php artisan ui bootstrap --auth
php artisan ui vue --auth
php artisan ui react --auth
```
