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
  <p class="home-hero__greeting">Game Dev · Graphics · Optimization</p>
  <h1 class="home-hero__title">개발 끄적대기</h1>
  <p class="home-hero__desc">게임 그래픽스, 렌더링, 성능 최적화에 대해 공부한 것들을 기록합니다. 틀릴 수 있고, 배우는 중입니다.</p>
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
{% assign featured_posts = site.posts | where: "featured", true | limit: 3 %}
{% if featured_posts.size == 0 %}
  {% assign featured_posts = site.posts | limit: 3 %}
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
     포트폴리오 섹션
     ──────────────────────────────────────────────────────
     ▶ 기본 카드 (이미지 없음):
       <div class="portfolio-card">
         <div class="portfolio-card__header">
           <span class="portfolio-card__title">이름</span>
           <span class="portfolio-card__role">역할</span>
         </div>
         <p class="portfolio-card__desc">설명</p>
         <div class="portfolio-card__tags">
           <span class="tag-chip">Unity</span>
         </div>
         <!-- 링크가 있으면: -->
         <!-- <a href="URL" class="portfolio-card__link">자세히 보기 →</a> -->
       </div>

     ▶ 이미지 있는 카드:
       1. /images/ 폴더에 이미지 파일 업로드
       2. 아래 구조 사용 (has-image 클래스 + __body 래퍼 필요)

       <div class="portfolio-card has-image">
         <div class="portfolio-card__body">
           <div class="portfolio-card__header">
             <span class="portfolio-card__title">이름</span>
             <span class="portfolio-card__role">역할</span>
           </div>
           <p class="portfolio-card__desc">설명</p>
           <div class="portfolio-card__tags">
             <span class="tag-chip">Unity</span>
           </div>
           <!-- <a href="URL" class="portfolio-card__link">자세히 보기 →</a> -->
         </div>
         <div class="portfolio-card__image">
           <img src="/images/파일명.jpg" alt="프로젝트명">
         </div>
       </div>
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
      게임 '하늘섬'은 2022년 청강문화산업대학교 졸업작품으로 개발한 액션 어드벤처 게임입니다. 하늘섬이라는 그래픽 컨셉과 단기간에 높은 완성도를 보여준 작품이라는 점에서 큰 관심을 받았습니다. Steam에서 무료로 플레이 가능합니다.
    </p>
    <div class="portfolio-card__tags">
      <span class="tag-chip">Unity URP</span>
      <span class="tag-chip">Student Project</span>
    </div>
    <a href="hhttps://store.steampowered.com/app/2302640/SkyIsland/" class="portfolio-card__link" target="_blank">자세히 보기 →</a>
  </div>
