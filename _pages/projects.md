---
layout: archive
tilte: 'My Projects'
permalink: /projects/
author_profile: true
---

Currently, I am realizing several machine learning projects, they are focused on deep learning for processing audio, text and videos in order to determine emotions in communication...

<br>
<br>

<div class="grid__wrapper">
    {% for post in site.posts %}
        {% if post.categories contains 'project' %}
            {% include archive-single.html type="grid" %}
        {% endif %}
    {% endfor %}
</div>