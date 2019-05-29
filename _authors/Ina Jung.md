---
title: Ina Jung
layout: post
author: Ina Jung
---

{% for post in site.posts %}
<!-- author 정보가 저자와 같은 경우만 리스트로 출력한다. -->
{% if post.author == page.author %}
<li>
  <h2>
    <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
  </h2>
  <section class="post-excerpt" itemprop="description">
    <p>{{ post.content | strip_html | truncatewords: 25 }}</p>
  </section>
  <section class="post-meta">
    <div class="post-date">{{ post.date | date: "%Y-%m-%d" }}</div>
    <div class="post-categories">
      {% if post.author %}
        {% for member in site.data.members %}
          {% if post.author == member.name %}
          <a href="{{ site.baseurl }}/authors/{{ post.author }}">{{member.name}}</a>
          {% endif %}
        {% endfor %}
      {% endif %}
    </div>
  </section>
</li>
{% if forloop.last == false %}
<hr>
{% endif %}

{% endif %}
{% endfor %}