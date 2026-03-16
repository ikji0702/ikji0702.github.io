---
permalink: /
layout: archive
title: ""
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

{% include base_path %}

<div class="home-hero">
  <p class="home-hero__greeting">Game Dev · Graphics</p>
  <h1 class="home-hero__title">개발 끄적대기</h1>
  <p class="home-hero__desc">게임 그래픽스에 대해 공부한 것들을 기록합니다.</br> 틀릴 수 있고, 배우는 중입니다.</p>
</div>

<!-- ======================================================
     추천 글 섹션
     추천 글 설정 방법:
       원하는 포스트의 front matter (---로 시작하는 상단 메타 정보)에
       아래 한 줄을 추가하면 이 섹션에 자동으로 표시됩니다:
         featured: true
       최대 3개가 표시되며, 날짜 역순으로 정렬됩니다.
       featured: true 인 글이 없으면 최신 글 3개가 대신 표시됩니다.
     ====================================================== -->
{% assign visible_posts = site.posts | where_exp: "p", "p.hidden != true" %}
{% assign featured_posts = visible_posts | where: "featured", true | limit: 3 %}
{% if featured_posts.size == 0 %}
  {% assign featured_posts = visible_posts | limit: 3 %}
{% endif %}

<div class="home-section-header">
  <h2 class="home-section-title">추천 글</h2>
  <a href="{{ base_path }}/posts/" class="home-view-all">모든 글 보기 →</a>
</div>

<div class="timeline">
{% for post in featured_posts %}
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

<!-- ======================================================
     포트폴리오 섹션 수정 방법:
       카드 추가/제거: portfolio-card 블록을 복사하거나 삭제하세요.
       이미지 추가: has-image 클래스 사용법은 assets/css/custom.css 섹션 30 참고.
     ====================================================== -->
<div class="home-section-header" style="margin-top:3em;">
  <h2 class="home-section-title">포트폴리오</h2>
</div>

<div class="portfolio-grid">

  <!-- 카드 1 -->
  <div class="portfolio-card">
    <div class="portfolio-card__header">
      <span class="portfolio-card__title">하늘섬 Skyisland</span>
      <span class="portfolio-card__role">AD / PM / Lighting Artist </span>
    </div>
    <p class="portfolio-card__desc">
      게임 '하늘섬'은 2022년 청강문화산업대학교 졸업작품으로 개발한 액션 어드벤처 게임입니다. Steam에서 무료로 플레이 가능합니다.
    </p>
    <div class="portfolio-card__tags">
      <span class="tag-chip">Unity URP</span>
      <span class="tag-chip">Student Project</span>
    </div>
    <a href="https://store.steampowered.com/app/2302640/SkyIsland/" class="portfolio-card__link" target="_blank">자세히 보기 →</a>
  </div>
