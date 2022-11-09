---
layout: annotation
title: "Chapter 1 Annotations"
permalink: /annotations01
number: "01"
language: en
---

<div class="annotation-text">
    <div id="annotations-en">
        {% for annotation in site.data.comments-01_en %}
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
        {% for annotation in site.data.comments-01_ru %}
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
