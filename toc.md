---
layout: page
title: Table of Contents
sort-order: 2
---

<div class="toc">
  <ul class="texts">
  {% for item in site.chapters %}
    {% if item.number %}
      {% assign chapterMatch = site.texts | where: "chapter-number", item.number %}
        {% assign englishMatch = chapterMatch | where: "language", "en" | first %}
          {% assign title_en = englishMatch.title %}
        {% assign russianMatch = chapterMatch | where: "language", "ru" | first %}
          {% assign title_ru = russianMatch.title %}
            <li class="text-title">
              <a href="{{ site.baseurl }}{{ item.url }}">
                {{ item.number }}. {{ title_en }}<span class="toc-ru"> / {{ title_ru }}</span>
              </a>
            </li>
    {% endif %}
  {% endfor %}
  </ul>
</div>