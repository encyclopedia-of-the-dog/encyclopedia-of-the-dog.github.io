---
layout: annotation
title: "Front Matter Annotations"
permalink: /annotations00
number: "00"
language: en
---

<div class="annotation-text">
    <div id="annotations-en">
        {% for annotation in site.data.comments-00_en %}
        <div id="{{ annotation.Id }}">
            <p markdown="1">
                <span class="highlighted">{{ annotation.highlighted }}</span> - {{ annotation.text }}
                {% assign list = annotation.tags %}
                {% assign tags = list | remove: "[" | remove: "]" | remove: "'" | split: ", " -%}
                {% for tag in tags -%}
                    <span class="tag tag-{{ tag }}">{{ tag }}</span> 
                {% endfor %}
            </p>
        </div>
        {% endfor %}
    </div>
    <div id="annotations-ru">
        {% for annotation in site.data.comments-00_ru %}
        <div id="{{ annotation.Id }}">
            <p markdown="1">
                <span class="highlighted">{{ annotation.highlighted }}</span> - {{ annotation.text }}
                {% assign list = annotation.tags %}
                {% assign tags = list | remove: "[" | remove: "]" | remove: "'" | split: ", " -%}
                {% for tag in tags -%}
                    <span class="tag tag-{{ tag }}">{{ tag }}</span> 
                {% endfor %}
            </p>
        </div>
        {% endfor %}
    </div>
</div>
