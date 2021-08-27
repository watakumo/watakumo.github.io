---
title: Kubernetesの実装１　
tags: [Kubernetes, Docker Swarm, Azure]
style:
color: primary
description: Kubernetesを分析してみました。
---

![](https://miro.medium.com/max/6000/1*qHvFfsb8YriqUsGe1Q9e9A.png)

ゼミの広告メールを受けて開いたら、kubernetesというものを初めて聞きました。

Dokcer Swarmとよく比較されるグーグルのOPENソースだそうです。

https://events19.linuxfoundation.org/events/kubernetes-forum-seoul-2019/

リナックス財団から運営している国際的なゼミだったなので、

親戚の結婚で一時帰国したついでに、参加したいと思って見ました。

でも、参加費だけで2万円を超えていました…。　

これはGNUの哲学とあっているんですかね。と貧乏人は悔しく思い…

やったついでにkubernetesについて調べることだけでもしてみました。

# kubernetesってそもそも何？

> Kubernetes is an open source container orchestration solution
> that is used for managing containerized software and services with a high degree of automation.
> [reference] https://www.nakivo.com/blog/docker-vs-kubernetes/

一言で、コンテイナーの　オーケストレーションの　ツールですね。

なるほど！　さっぱりわかりません。

ゴーグルで作ってOPENソースとして今はリナックス財団で担当しているそうです。

Docker Swarmとよく比較されます。　入門はDocker　Swarmのほうが簡単だそうです。


# オーケストレーションはなぜやるの？

Dockerのようなコンテイナー化さたデプロイ環境で、ある問題点がありました。

複数のコンテイナーが使われるときに、どうやって調整して、スケジューリングされるのか、

またお互いにどうやって通信するのか、拡張はどうなのか？などの問題でした。

このため現れたのが　**コンテイナーオーケストレーション** なんです。


# 使いところ

ある企業で、三つのアプリケーションをDevOpsで開発しているとします。

さーばはAとBの2台を使っていてDockerのホストは三つ、使っているコンテイナーは10個です。

イメージを作っておいたおかげで、AとBの構築はDockerで簡単にできました。

でも、時間が立って、プロジェクトごとの仕様が変わりました。

また、コンテイナー間のヴァージョン交換で使えなくなったり、止まったりします。

つまりコンテイナーたちで下記のような管理をしたいと思うようになります。

- プロビジョニング（実行予約）
- より簡単に構成スクリプトで作成
- モニタリング（障害時に、再起動なの）
- アップデートとロールバック(コンテイナークラスター全体を)
- 探索（独立し、動的にMYSQLのインスタンスをRealTime探索）
- コンテイナーポリシー管理(どのサーバで実行するか、CPU１つごとに何個のコンテイナーを使うか)
- 拡張(既存のITツールとも利用可能にする)

# クラウドサーバ上での使い

基本、クラウドサーバのサービスではKubernetesをすでに移植されているので

使うことが可能です。

<https://docs.microsoft.com/ja-jp/azure/aks/intro-kubernetes>

# kubernetes OR Docker Swarm ？!

韓国では、物理サーバは立ち上げていないので（日本では Raspberry PIのサーバが一つあるけど…）

AZUREで使ってみることにしました。

どっちが使いやすいのかは…、まずはやってみて判断してみましょう。

続きは後で…
