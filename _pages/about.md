---
permalink: /
layout: archive
title: false
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

{% include base_path %}

<div class="home-hero">
  <p class="home-hero__greeting">안녕하세요 👋</p>
  <h1 class="home-hero__title">개발 끄적대기</h1>
  <p class="home-hero__desc">게임 그래픽스, 렌더링, 최적화에 대해 공부한 것들을 기록합니다.</p>
</div>

<div class="home-section-header">
  <h2 class="home-section-title">최근 글</h2>
  <a href="{{ base_path }}/posts/" class="home-view-all">모든 글 보기 →</a>
</div>

<div class="timeline">
{% for post in site.posts limit:5 %}
  <div class="timeline-item">
    <div class="timeline-date">{{ post.date | date: "%m.%d" }}</div>
    <div class="timeline-content">
      <h3 class="timeline-title">
        <a href="{{ base_path }}{{ post.url }}">{{ post.title }}</a>
      </h3>
      <div class="timeline-meta">
        {% if post.read_time %}
          <span class="read-time"><i class="fa fa-clock-o" aria-hidden="true"></i> {% include read-time.html %}</span>
        {% endif %}
        {% for tag in post.tags %}
          <a href="{{ base_path }}/tags/#{{ tag | slugify }}" class="tag-chip">{{ tag }}</a>
        {% endfor %}
      </div>
    </div>
  </div>
{% endfor %}
</div>
