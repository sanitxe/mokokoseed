---
layout: default
title: "Una's Reputation Guide"
description: "Use this guide to quickly view various rewards to Una's Reputation, and keep track of ones that have already been completed."
---

<h1>Una's Reputation Guide</h1>

<div class="progressbar-container">
  <div class="progressbar-bar"></div>
  <div class="progressbar-label"></div>
</div>
<div class = "ready"></div>

<table id="sortTable">
  <thead>
    <tr>
      <th class="no-sort"></th>
      <th>Reputation</th>
      <th data-toggle="tooltip" data-placement="top" title="Minimum days to acquire."><i style="font-size:30px" class="las la-calendar-day"></i></th>
      <th>Quests</th>
      <th>Coin</th>
      <th>Emote</th>
      <th>Potion</th>
      <th>Craft</th>
      <th>Collection</th>
      <th>Mount</th>
      <th>Card</th>
      <th>Island Token</th>
      <th>Other</th>
    </tr>
  </thead>
  <tbody>
    {% for reputation in site.data.una %}
      <tr class="dt-hasChild parent">
        <td>
          <input type="checkbox" id="{{ reputation.id }}" class="box">
        </td>
        <td> 
          <img class="lost-icon" src="/assets/img/icon/una.png" /> {{ reputation.name }}
        </td>
        <td> 
          <span data-toggle="tooltip" data-placement="top" title="Minimum days to acquire.">{{ reputation.days }}</span>
        </td>  
        <td>
          <small>{{ reputation.quests }}</small>
        </td>
        <td>{% if reputation.silver > 0 %}{{ reputation.silver }} <img class="lost-icon" src="/assets/img/icon/silver.png" />{% endif %}
        {% if reputation.pirate > 0 %}{{ reputation.pirate }} <img class="lost-icon" src="/assets/img/icon/pirate.png" />{% endif %}</td>
        <td>{% if reputation.emote != nil %}<img class="lost-icon" src="/assets/img/icon/emote.png" /> {{ reputation.emote }}{% endif %}</td>
        <td>{% if reputation.potion != nil %}<img class="lost-icon" src="/assets/img/icon/{{ reputation.potion }}.png" /> {{ reputation.potion }}{% endif %}</td>
        <td>{% if reputation.craft != nil %}<img class="lost-icon" src="/assets/img/icon/crafting.png" /> Crafting Recipe: {{ reputation.craft }}{% endif %}</td>
        <td>{% if reputation.collect != nil %}{{ reputation.collect }} {% endif %}</td>
        <td>{% if reputation.mount != nil %}{{ reputation.mount }} {% endif %}</td>
        <td>{% if reputation.card != nil %}<img class="lost-icon" src="/assets/img/icon/card.png" /> {{ reputation.card }} {% endif %}</td>
        <td>{% if reputation.island != nil %}<img class="lost-icon" src="/assets/img/icon/island.png" /> {{ reputation.island }} {% endif %}</td>
        <td>{% if reputation.other != nil %}{{ reputation.other }} {% endif %}</td>
      </tr>
    {% endfor %}
  </tbody>
</table>
