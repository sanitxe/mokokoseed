---
layout: default
title: "Main/World Questline Guide"
description: "Use this guide to reference how far you've completed the various World questlines on Lost Ark."
---

<h1>Main/World Questline Guide</h1>
{% for quest in site.data.questline %}
<h3>{{ quest.area }}</h3>
<ol>
  {% for entry in quest.quests %}
  <li>{{ entry.quest }}</li>
  {% endfor %}
</ol>

{% endfor %}
{% for quest in site.data.questline %}
<div class="d-flex align-items-start">
  <div class="nav flex-column nav-pills me-3" id="v-pills-tab" role="tablist" aria-orientation="vertical">
    <button class="nav-link" id="v-pills-{{ quest.area }}-tab" data-bs-toggle="pill" data-bs-target="#v-pills-{{ quest.area }}" type="button" role="tab">{{ quest.area }}</button>
  </div>
  <div class="tab-content" id="v-pills-tabContent">
    <div class="tab-pane fade" id="v-pills-{{ quest.area }}" role="tabpanel">
    <ol>
    {% for entry in quest.quests %}
    <li>{{ entry.quest }}</li>
    {% endfor %}
    </ol>
    </div>
  </div>
</div>
{% endfor %}
