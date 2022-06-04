---
layout: default
title: "Main/World Questline Guide"
description: "Use this guide to reference how far you've completed the various World questlines on Lost Ark."
---


<h1>Main/World Questline Guide</h1>
<div class="d-flex align-items-start">
  <div class="nav flex-column nav-pills col-4" id="Main-Quest-Pill" style="max-width:370px" role="tablist" aria-orientation="vertical">
    {% for quest in site.data.questline %}
    
<div id="carousel-{{ quest.area | slugify  }}" class="carousel slide" data-interval="false" style="display:none;max-width:370px" data-ride="carousel">
  <div class="carousel-inner">
    {% for img in quest.images %}
    <div class="carousel-item {% if img.first == true %}active{% endif %}">
      <img class="d-block w-100" src="/assets/img/main-quest/{{ img.image }}">
    </div>
    {% endfor %}
  </div>
  <a class="carousel-control-prev" href="#carousel-{{ quest.area | slugify  }}" role="button" data-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="sr-only">Previous</span>
  </a>
  <a class="carousel-control-next" href="#carousel-{{ quest.area | slugify  }}" role="button" data-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="sr-only">Next</span>
  </a>
</div>    
    
    {% endfor %}


    {% for quest in site.data.questline %}

    <button class="nav-link questline-tab {% if quest.area == 'Rethramis' %}active{% endif %}" id="{{ quest.area | slugify  }}-tab" data-toggle="pill" data-target="#{{ quest.area | slugify  }}" type="button" role="tab">{{ quest.area }}</button>
    {% endfor %}
  </div>
  <div class="tab-content">
    {% for quest in site.data.questline %}
    <div id="{{ quest.area | slugify }}" class="tab-pane fade {% if quest.area == 'Rethramis' %}show active{% endif %} {{ quest.area | slugify }}" role="tabpanel">
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
jQuery(document).ready(function($){
  $('#carousel-rethramis').show();
{% for quest in site.data.questline %}
  $('#{{ quest.area | slugify  }}-tab').click(function(){
    $('.carousel').hide();
    $('#carousel-{{ quest.area | slugify  }}').show();
  });
{% endfor %}
});

$('.progress-steps').each((_, progress) => { const steps = $('> div.right > div', progress); steps.each((i, el) => $(el).mouseenter(e => onHover(el))); const onHover = (el) => { steps.removeClass(['current', 'prev']); el.classList.add('current'); $(el).prevAll().slice(1).addClass('prev'); }; })
</script>
