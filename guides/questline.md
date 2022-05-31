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

<div class="d-flex align-items-start">
  <div class="nav flex-column nav-pills me-3" id="myTab" role="tablist" aria-orientation="vertical">
    {% for quest in site.data.questline %}
    <button class="nav-link" id="{{ quest.area }}-tab" data-toggle="pill" href="{{ quest.area }}" type="button" role="tab">{{ quest.area }}</button>
    {% endfor %}
  </div>
  <div class="tab-content" id="v-pills-tabContent">
    {% for quest in site.data.questline %}
    <div class="tab-pane fade {% if quest.area == 'Tortoyk' %}active {% endif %}" id="{{ quest.area }}" role="tabpanel">
    <ol>
    {% for entry in quest.quests %}
    <li>{{ entry.quest }}</li>
    {% endfor %}
    </ol>
    </div>
    {% endfor %}
  </div>
</div>

