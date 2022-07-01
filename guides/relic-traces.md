---
layout: default
title: "Relic Trace Maps"
description: "Collection of maps for finding Relic Traces in Lost Ark."
---

<h1>Relic Trace Maps</h1>

<div class="nav nav-tabs" id="Relic-tab" role="tablist" aria-orientation="vertical">
  {% for relic in site.data.relic-trace %}
  <a class="nav-link {% if relic.area == 'Arthetine' %}active{% endif %}" id="{{ relic.area | slugify }}-tab" data-toggle="tab" href="#{{ relic.area | slugify }}-content" role="tab">{{ relic.area }}</a>
  {% endfor %}
</div>
<div class="tab-content" id="Relic-tabContent">
  {% for relic in site.data.relic-trace %}
  <div class="tab-pane fade {% if relic.area == 'Arthetine' %}show active{% endif %}" id="{{ relic.area | slugify }}-content" role="tabpanel">
    <div class="row">
    <div class="col-3">
      <div class="nav flex-column nav-pills" id="v-pills-tab" role="tablist" aria-orientation="vertical">
      {% for map in relic.maps %}
        <img src="/assets/img/map-icons/{{ map.name }}.png" class="badge"><a class="nav-link {% if map.first == true %}active{% endif %}" id="{{ map.name | slugify }}-tab" data-toggle="pill" href="#{{ map.name | slugify }}-tabContent" role="tab">{{ map.name }}</a>
      {% endfor %}
      </div>
    </div>
    <div class="col-9">
    <div class="tab-content" id="{{ relic.area | slugify }}-maps">
      {% for map in relic.maps %}
      <div class="tab-pane fade {% if map.first == true %}show active{% endif %}" id="{{ map.name | slugify }}-tabContent" role="tabpanel">
        <img src="/assets/img/relic-trace/{{ relic.area }} - {{ map.name }}.png">
      </div>
      {% endfor %}
    </div>
    </div>
    </div>
  </div>
  {% endfor %}
</div>
