---
layout: default
title: "Main/World Questline Guide"
description: "Use this guide to reference how far you've completed the various World questlines on Lost Ark."
---


<h1>Main/World Questline Guide</h1>
<div class="d-flex align-items-start">
  <div class="nav flex-column nav-pills col-4" id="myPill" role="tablist" aria-orientation="vertical">
    {% for quest in site.data.questline %}
    <button class="nav-link questline-tab" id="{{ quest.area }}-tab" data-toggle="pill" href="#{{ quest.area }}" type="button" role="tab">{{ quest.area }}</button>
    {% endfor %}
  </div>
  <div class="tab-content">
    {% for quest in site.data.questline %}
    <div class="tab-pane fade {% if quest.area == 'Tortoyk' %}show active{% endif %}" id="{{ quest.area }}" role="tabpanel">
    <div class="outer">
      <div class="progress-steps">
      <div class="right">
      {% for entry in quest.quests %}
          <div {% if entry.last == true %}class="done"{% endif %} {% if entry.first == true %}class="current"{% endif %}>{{ entry.quest }}</div>
      {% endfor %}
      </div>
    </div>  
    </div>  
    </div>
    {% endfor %}
  </div>
</div>

<script>
  
// Test code

$('.progress-steps').each((_, progress) => {
  
  const steps = $('> div.right > div', progress);

  steps.each((i, el) => $(el).mouseenter(e => onHover(el)));

  const onHover = (el) => {
      steps.removeClass(['current', 'prev']);
      el.classList.add('current');
      $(el).prevAll().slice(1).addClass('prev');
    };
})

</script>
