---
layout: annotation
title: "Annotations"
permalink: /annotations
---

<div class="annotation-text">
    {% for annotation in site.data.chTwoRu %}
    <div id="{{ annotation.Id }}">
        <p markdown="1"><span class="highlighted">{{ annotation.highlighted }}</span> - {{ annotation.text }}</p>
    </div>
    {% endfor %}
</div>
