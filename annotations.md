---
layout: annotation
title: "Annotations"
permalink: /annotations
---

<div class="annotation-text">
    {% for annotation in site.data.chTwoRu %}
    <div id="{{ annotation.Id }}">
        <p markdown="1">
            <span class="highlighted">{{ annotation.highlighted }}</span> - {{ annotation.text }}
            {% assign list = annotation.tags %}
            {% assign tags = list | split: ", " -%}
            {% for tag in tags -%}
                <span class="tag tag-{{ tag }}">{{ tag }}</span> 
            {% endfor %}
        </p>
    </div>
    {% endfor %}
</div>
