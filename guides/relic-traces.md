---
layout: default
title: "Relic Trace Maps"
description: "Collection of maps for finding Relic Traces in Lost Ark."
---

<h1>Relic Trace Maps</h1>

<div class="nav flex-column nav-tabs" id="Relic-tab" role="tablist" aria-orientation="vertical">
  {% for relic in site.data.relic-trace %}
  <a class="nav-link {% if relic.area == 'Arthetine' %}active{% endif %}" id="{{ relic.area | slugify }}-tab" data-toggle="tab" href="#{{ relic.area | slugify }}-content" role="tab">{{ relic.area }}</a>
  {% endfor %}
</div>
<div class="tab-content" id="Relic-tabContent">
  {% for relic in site.data.relic-trace %}
  {% for map in relic.maps %}
  <div class="tab-pane fade {% if relic.area == 'Arthetine' %}show active{% endif %}" id="{{ relic.area | slugify }}-content" role="tabpanel">
    <img src="/assets/img/relic-trace/{{ relic.area }} - {{ map.name}}.png">
  </div>
  {% endfor %}
  {% endfor %}
</div>
