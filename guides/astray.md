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
    <li><img src="/assets/icons/{{ craft.item }}.png"> {{ craft.item }}</li>
    <li>{{ craft.quantity }}</li>
    {% for sub in craft.method %}
      <ul>
        <li> {{ sub.recipe }} </li>
        <li> {{ sub.quantity }} </li>
      </ul>
    {% endfor %}
  {% endfor %}
</ul>
