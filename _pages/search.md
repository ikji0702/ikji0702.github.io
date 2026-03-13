---
layout: archive
title: "검색"
permalink: /search/
author_profile: true
---

{% include base_path %}

<div class="search-page">
  <div class="search-box">
    <input type="text" id="search-query" placeholder="제목, 내용, 태그 검색..." autofocus />
  </div>
  <div id="search-results"></div>
</div>

<script>
var posts = [
  {% for post in site.posts %}
  {
    title: "{{ post.title | escape }}",
    url: "{{ post.url | prepend: site.baseurl }}",
    date: "{{ post.date | date: '%Y-%m-%d' }}",
    tags: [{% for tag in post.tags %}"{{ tag | escape }}"{% unless forloop.last %},{% endunless %}{% endfor %}],
    excerpt: "{{ post.excerpt | strip_html | escape | truncate: 180 }}"
  }{% unless forloop.last %},{% endunless %}
  {% endfor %}
];

document.addEventListener('DOMContentLoaded', function() {
  var input = document.getElementById('search-query');
  var container = document.getElementById('search-results');

  function render(results) {
    if (!results.length) {
      container.innerHTML = '<p class="search-empty">검색 결과가 없습니다.</p>';
      return;
    }
    container.innerHTML = results.map(function(p) {
      var tags = p.tags.map(function(t) {
        return '<span class="tag-chip">' + t + '</span>';
      }).join('');
      return '<div class="search-result-item">' +
        '<h3><a href="' + p.url + '">' + p.title + '</a></h3>' +
        '<div class="search-result-meta">' + p.date +
          (tags ? ' &nbsp; ' + tags : '') + '</div>' +
        (p.excerpt ? '<div class="search-result-excerpt">' + p.excerpt + '</div>' : '') +
        '</div>';
    }).join('');
  }

  input.addEventListener('input', function() {
    var q = input.value.toLowerCase().trim();
    if (!q) { container.innerHTML = ''; return; }
    var results = posts.filter(function(p) {
      return p.title.toLowerCase().includes(q) ||
             p.excerpt.toLowerCase().includes(q) ||
             p.tags.some(function(t) { return t.toLowerCase().includes(q); });
    });
    render(results);
  });
});
</script>
