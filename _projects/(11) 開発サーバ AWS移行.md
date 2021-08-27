---
name: 開発サーバ AWS移行(調査・見積)
tools: [Linux,AWS Codepipline,AWS EC2(AMI)]
image: https://www.easyredmine.com/images/articles/p14/f3751/logo.jpg
description: 社内開発サーバで利用中のシステムをAWSのサービスとGitHubへ移行
---

# 映画チケット購入アプリ開発

{% include elements/highlight.html text="テスターを超えた解決者としての役割" %}

---
{% include elements/list.html title="概要" %}
- 調査(影響、見積もり、チーム連携と調整)と移行計画作成 
- GitBucketからGitHubへ移行(80件以上、shell script)
- RedmineをAWS AMIへ移行(データマイグレイション、プラグイン切り替え)

{% include elements/list.html title="期間" %}
2021.01 ~ 2021.01 (1ヶ月)

{% include elements/list.html title="チーム人数（職位）" %}
単独開発

{% include elements/list.html title="担当業務" %}
調査

移行作業
- Linux
- AWS Codepipline - AWS EC2(AMI)


{% include elements/list.html title="開発サーバをクラウド化" %}

１０年近く使われていたサーバであるため、gitレポジトリやcgi、redmine、CIなどが複雑に絡んでいました。

{% include elements/list.html title="成果" %}

redmineのクラウド化
-　AWS見積もり(lightsailとEc2運用の比較)
-　プラグイン移行計画の立て方 

{% include elements/list.html title="感じたこと・学んだこと" %}

基盤システムを常に管理することでチームの効率も上げられると感じました。

何年ぶりにいきなり管理しようとすると、かなり大変なことになることを学べる機会でした。
