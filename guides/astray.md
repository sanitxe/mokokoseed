---
  title: Astray Crafting Guide
---

<div class="progress">
  <div class="progress-bar" role="progressbar" aria-valuenow="15" aria-valuemin="0" aria-valuemax="100"></div>
  <div class="progress-bar bg-success" role="progressbar"  aria-valuenow="30" aria-valuemin="0" aria-valuemax="100"></div>
  <div class="progress-bar bg-info" role="progressbar" aria-valuenow="20" aria-valuemin="0" aria-valuemax="100"></div>
</div>

<ul>
  {% for craft in site.data.astray %}
  <div class="input-group-prepend">
    <span class="input-group-text"><img src="/assets/icons/{{ craft.item }}.png"> {{ craft.item }}</span>
  </div>
  
  <div class="input-group mb-3">
    <input type="text" class="form-control" placeholder="{{ craft.item }}" aria-label="{{ craft.item }}" aria-describedby="basic-addon2">
    <div class="input-group-append">
      <span class="input-group-text" id="basic-addon2">/{{ craft.quantity }}</span>
    </div>
  </div>

{% for sub in craft.method %}
<ul>
<li> {{ sub.recipe }} </li>
<li> {{ sub.quantity }} </li>
</ul>
{% endfor %}
{% endfor %}
</ul>
