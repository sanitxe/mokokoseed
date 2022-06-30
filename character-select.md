---
layout: default
title: "Lost Ark Character Select Backgrounds"
description: "A collection of Lost Ark's Character Selection backgrounds."
---

<div class="card-deck">
{% for bg in site.data.wallpaper %}
  <div class="card">
    <img class="card-img-top emote-card" src="/assets/img/wallpaper/wallpaper_icon_{{ bg.icon }}.png">
    <div class="card-body">
      <h5 class="card-title">{{ bg.title }}</h5>
      <p class="card-text">{{ bg.desc }}</p>
    </div>
  </div>
{% endfor %}
</div>
