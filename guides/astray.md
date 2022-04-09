---
  title: Astray Crafting Guide
---

<div class="progress">
  <div class="progress-bar" role="progressbar" aria-valuenow="15" aria-valuemin="0" aria-valuemax="100"></div>
  <div class="progress-bar bg-success" role="progressbar"  aria-valuenow="30" aria-valuemin="0" aria-valuemax="100"></div>
  <div class="progress-bar bg-info" role="progressbar" aria-valuenow="20" aria-valuemin="0" aria-valuemax="100"></div>
</div>

{% for craft in site.data.astray %}
{% if craft.item != "Uncommon Ship Parts Material" %}
<div class="input-group my-3">
  <div class="input-group-prepend">
    <span class="input-group-text"><img src="/assets/img/icon/{{ craft.icon }}.png"> {{ craft.item }}</span>
  </div>  
  <input id="{{ craft.icon }}" type="text" class="form-control" aria-label="{{ craft.item }}" aria-describedby="basic-addon2">
  <div class="input-group-append">
    <span class="input-group-text" id="basic-addon2">/{{ craft.quantity }}</span>
  </div>
</div>
{% for sub in craft.method %}
<div class="input-group my-3 mx-5 sub-recipe-item">
  <div class="input-group-prepend">
    <span class="input-group-text"><img src="/assets/img/icon/{{ sub.icon }}.png"> {{ sub.recipe }}</span>
  </div>  
  <input id="{{ craft.icon }}" type="text" class="form-control" aria-label="{{ sub.recipe }}" aria-describedby="basic-addon2">
  <div class="input-group-append">
    <span class="input-group-text" id="basic-addon2">/{{ sub.quantity }}</span>
  </div>
</div>
{% endfor %}
{% endif %}
{% endfor %}

<div class="progress">
  <div class="progress-bar" role="progressbar" aria-valuenow="15" aria-valuemin="0" aria-valuemax="100"></div>
  <div class="progress-bar bg-success" role="progressbar"  aria-valuenow="30" aria-valuemin="0" aria-valuemax="100"></div>
  <div class="progress-bar bg-info" role="progressbar" aria-valuenow="20" aria-valuemin="0" aria-valuemax="100"></div>
</div>

{% for craft in site.data.astray %}
{% if craft.item == "Uncommon Ship Parts Material" %}
<div class="input-group my-3">
  <div class="input-group-prepend">
    <span class="input-group-text"><img src="/assets/img/icon/{{ craft.icon }}.png"> {{ craft.item }}</span>
  </div>  
  <input id="{{ craft.icon }}" type="text" class="form-control" aria-label="{{ craft.item }}" aria-describedby="basic-addon2">
  <div class="input-group-append">
    <span class="input-group-text" id="basic-addon2">/{{ craft.quantity }}</span>
  </div>
</div>
{% for sub in craft.method %}
<div class="input-group my-3 mx-5 sub-recipe-item">
  <div class="input-group-prepend">
    <span class="input-group-text"><img src="/assets/img/icon/{{ sub.icon }}.png"> {{ sub.recipe }}</span>
  </div>  
  <input id="{{ craft.icon }}" type="text" class="form-control" aria-label="{{ sub.recipe }}" aria-describedby="basic-addon2">
  <div class="input-group-append">
    <span class="input-group-text" id="basic-addon2">/{{ sub.quantity }}</span>
  </div>
</div>
{% endfor %}
{% endif %}
{% endfor %}
