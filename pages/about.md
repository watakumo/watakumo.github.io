---
layout: page
title: About
permalink: /about/
weight: 3
---

# **About Me**

はじめまして **{{ site.author.name }}**　と申します。<br>
自分の強みを３つの言葉で表現すると、「推進力」「分析力」「努力」だと思います。<br>
IT技術を生かして日本でやりたいことが山ほどあります。<br>
また、日本社会の一員として日本の文化を尊重し、共に生き、成長したい気持ちが高いです。

<div class="row">
{% include about/skills.html title="Programming Skills" source=site.data.programming-skills %}
{% include about/skills.html title="Other Skills" source=site.data.other-skills %}
</div>

<div class="row">
{% include about/timeline.html %}
</div>
