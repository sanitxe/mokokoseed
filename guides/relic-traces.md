---
layout: default
title: "Relic Trace Maps"
description: "Collection of maps for finding Relic Traces in Lost Ark."
---

<h1>Relic Trace Maps</h1>

<div class="nav flex-column nav-pills" id="v-pills-tab" role="tablist" aria-orientation="vertical">
  {% for relic in site.data.relic-trace %}
  <a class="nav-link {% if relic.area == 'Arthetine' %}active{% endif %}" id="v-pills-home-tab" data-toggle="pill" href="#v-pills-home" role="tab">{{ relic.area }}</a>
  {% endfor %}
</div>
<div class="tab-content" id="v-pills-tabContent">
  {% for map in relic.maps %}
  <div class="tab-pane fade {% if relic.area == 'Arthetine' %}show active{% endif %}" id="v-pills-home" role="tabpanel" aria-labelledby="v-pills-home-tab"><img src=""></div>
  {% endfor %}
</div>
