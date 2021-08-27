---
title: GoogleマップとCrawling
tags: [GCP, Map, Node, NPM]
style: 
color: primary
description: GoogleマップのClusterとHTMLをコピー
---

今日は、ちょっと寄り道の日です。

時間がまた余っていたので、Nodeプログラミングをしました。

# 考え
Googleマップはよく使われる機能ですね。

サイトからの一覧位置情報を視覚的に地図に見せるのは

いいと思います。でもデータが多いと？

見ずらくなりますね。

そこで出るのがClusterという概念です。

ライブラリを出ているので、素早く実装できます。

ただ、今回はベースになるデータがありましたので、

Crawlingをしてデータを作ろうとしました。

# 参考
GMAPの動作が見られます。位置を任意で入れました。
<https://watakumo.github.io/noFrame_GmapCluster_Crawling/>

Nodeで作ったところは、gitHubで確認できます。
<https://github.com/watakumo/noFrame_GmapCluster_Crawling/blob/master/app.js>

# 最後
FrameWorkなしの開発って、やはり色々難しいですね。

次からはNodeプログラミングでしたら、Expressを使ったほうがよさそうです。
