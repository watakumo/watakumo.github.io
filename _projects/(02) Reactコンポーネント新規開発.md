---
name: Reactコンポーネント新規開発
tools: [JavaScript(ES6), JSX(React), HTML5, SASS, NodeJS(npm), git]
image: https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcT-g86Qs_v6bIGeQA3IPXStYNCRLInySf331-Mo60o3MQe7Dw6r
description: 新技術導入によるフロント部品開発
---

# Reactコンポーネント新規開発

{% include elements/highlight.html text="新技術導入によるフロント部品開発" %}


---
{% include elements/list.html title="概要" %}
新フレイムワーク導入としてReactを使うことになり、

今後のプロジェクトに使われる共通部品を開発した社内開発業務


{% include elements/list.html title="期間" %}
2017.05 ~ 2017.05 (一ヶ月)

{% include elements/list.html title="チーム人数（職位）" %}
５人（メンバー）

{% include elements/list.html title="担当業務" %}
カレンダーとラベルボックスなどのベース部品を新規開発

{% include elements/list.html title="ES6を使っての開発" %}
![preview](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcTPBDqhC-qpnjlXi0jndjP70FLo6zdzJfhXGT-REGIPZA4a_jNN)

https://github.com/lukehoban/es6features

OJTの社内システム開発スケジュールが終わったある日、

ある先輩から頼みが入りました。

「ワンちゃんってさ。JSできるだよね。これ手伝って。」

それで拝見したコードが下記のようなコード

``` javascript
let Func = (a, b = 10) => {
 return a + b;
}
Func(20); // 20 + 10 = 30

import React, { Component } from 'react';
import { Frame } from '../base/Frame';
import PortalList from './PortalList';

class Portal extends Component {

  componentDidMount() {
  }

  render() {
    return (
      <Frame showNav={true}>
        <PortalList />
      </Frame>
    );
  }
}

export default Portal;
```
ES6でした。妙にJAVAと似ていて実はJS。ショックでした。

NodeJSと共にES6でReactのコンポーネントを作り出すために

退社しても[資料](https://github.com/lukehoban/es6features)を
参考しました。



Coding規約としては業務指示通り[airBnbのガイド](https://github.com/airbnb/javascript)を参考しました。

{% include elements/list.html title="成果" %}
元々は1か月の開発スケジュールでしたが、3週で完成できました。

残り一週の時間はES6の勉強をして頂きました。

{% include elements/list.html title="感じたこと・学んだこと" %}

右も左も分からないしろうとでしたが、一人で学習しながら実務に適用する喜びが分かりました。

ES6で文法Sugarとしてのclassの使い方やlet・const などの変数のスコープ、literal templateなどを学びました。

JqueryなしでのPure Javascriptに関心を持つきっかけになりました。
