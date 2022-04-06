---
  title: Astray Crafting Guide
---

<ul>
  {% for craft in site.data.astray %}
    <li><img src="/assets/icons/{ craft.item }.png"> { craft.item }</li>
    <li>{ craft.quantity }</li>
    {% for sub in craft.method %}
      <ul>
        <li> { sub.recipe }
        <li> { sub.quantity }
      </ul>
    {% endfor %}
  {% endfor %}
<ul>
