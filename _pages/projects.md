---
title: Portfolio and projects
layout: archive
permalink: /projects/
author_profile: true
---


A series of projects I realized and I currently realize...

<div class="grid__wrapper">
    {% for post in site.posts %}
        {% if post.categories contains 'projects' %}
            {% include archive-single.html type="grid" %}
        {% endif %}
    {% endfor %}
</div>
