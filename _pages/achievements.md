---
layout: page
title: Achievements
permalink: /achievements/
description: My achievements
nav: true
nav_order: 4

horizontal: true
---

<!-- pages/achievements.md -->
{% assign achievements = site.achievements | sort: 'date' | reverse %}

{% for achievement in achievements %}
  {% include achievements.html %}
{% endfor %}
