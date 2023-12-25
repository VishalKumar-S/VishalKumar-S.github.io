---
layout: page
title: Achievements
permalink: /achievements/
description: My achievements
nav: true 
nav_order: 4
---

<div class="container">
  <div class="row">
    {% assign achievements = site.achievements | sort 'date' | reverse %}
    {% for achievement in achievements %}
      <div class="col-lg-6 mb-4">
        {% include achievements.html %}
      </div>
    {% endfor %}
  </div>
</div>
