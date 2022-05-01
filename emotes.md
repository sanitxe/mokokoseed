---
layout: default
title: "Lost Ark Emotes"
description: "A collection of transparent Lost Ark Emotes for use. Add them to your Discord servers and don't forget to say LAILAI"
---

<div class="card-deck">
{% for emote in site.data.emotes %}
  <div class="card">
    <img class="card-img-top emote-card" src="/assets/img/emotes/emoji_a_{{ emote.id }}.png">
    <div class="card-body">
      <h5 class="card-title">[{{ emote.line }}]</h5>
      <p class="card-text">{{ emote.desc }}</p>
    </div>
  </div>
{% endfor %}
</div>
