---
layout: default
title: "Main/World Questline Guide"
description: "Use this guide to reference how far you've completed the various World questlines on Lost Ark."
---


<h1>Main/World Questline Guide</h1>
<div class="d-flex align-items-start">
  <div class="nav flex-column nav-pills me-3" id="myPill" role="tablist" aria-orientation="vertical">
    {% for quest in site.data.questline %}
    <button class="nav-link" id="{{ quest.area }}-tab" data-toggle="pill" href="#{{ quest.area }}" type="button" role="tab">{{ quest.area }}</button>
    {% endfor %}
  </div>
  <div class="tab-content">
    {% for quest in site.data.questline %}
    <div class="tab-pane fade {% if quest.area == 'Tortoyk' %}show active{% endif %}" id="{{ quest.area }}" role="tabpanel">
    <div class="outer">
      <div class="progress-steps">
      <div class="right">
      {% for entry in quest.quests %}
          <div>{{ entry.quest }}</div>
      {% endfor %}
      </div>
    </div>  
    </div>  
      
    <ol>
    {% for entry in quest.quests %}
    <li>{{ entry.quest }}</li>
    {% endfor %}
    </ol>
    </div>
    {% endfor %}
  </div>
</div>

