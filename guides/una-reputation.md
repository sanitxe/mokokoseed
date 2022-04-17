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
      <th class="npc-icon-column no-sort"></th>
      <th>Reputation</th>
      <th data-toggle="tooltip" data-placement="top" title="Minimum days to acquire."><i style="font-size:30px" class="las la-calendar-day"></i></th>
      <th>Quests</th>
      <th>Levels</th>
      <th>Silver</th>
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
      <tr>
        <td>
          <input type="checkbox" id="{{ reputation.id }}" class="box">
        </td>
        <td>
            <img class="islands-icon" src="/assets/img/icon/una.png" />
        </td>
        <td> 
          {{ reputation.name }}
        </td>
        <td> 
          <span data-toggle="tooltip" data-placement="top" title="Minimum days to acquire.">{{ reputation.days }}</span>
        </td>  
        <td>
          {{ reputation.quests }}
        </td>
        <td>
          <small>
          {% if reputation.rep1 > 0 %}Level 1: /{{ reputation.rep1 }}<br />{% endif %}
          {% if reputation.rep2 > 0 %}Level 2: /{{ reputation.rep2 }}<br />{% endif %}
          {% if reputation.rep3 > 0 %}Level 3: /{{ reputation.rep3 }}<br />{% endif %}
          {% if reputation.rep4 > 0 %}Level 4: /{{ reputation.rep4 }}<br />{% endif %}
          {% if reputation.rep5 > 0 %}Level 5: /{{ reputation.rep5 }}<br />{% endif %}
          {% if reputation.rep6 > 0 %}Level 6: /{{ reputation.rep6 }}{% endif %}
          </small>
        </td>
        <td>{% if reputation.silver > 0 %}{{ reputation.silver }} Silver{% endif %}</td>
        <td>{% if reputation.emote != nil %}<img class="lost-icon" src="/assets/img/icon/emote.png" />{{ reputation.emote }}{% endif %}</td>
        <td>{% if reputation.potion != nil %}<img class="lost-icon" src="/assets/img/icon/{{ reputation.potion }}.png" />{{ reputation.potion }}{% endif %}</td>
        <td>{% if reputation.craft != nil %}<img class="lost-icon" src="/assets/img/icon/crafting.png" />{{ reputation.craft }}{% endif %}</td>
        <td>{% if reputation.collect != nil %}{{ reputation.collect }} {% endif %}</td>
        <td>{% if reputation.mount != nil %}{{ reputation.mount }} {% endif %}</td>
        <td>{% if reputation.card != nil %}<img class="lost-icon" src="/assets/img/icon/card.png" />{{ reputation.card }} {% endif %}</td>
        <td>{% if reputation.island != nil %}<img class="lost-icon" src="/assets/img/icon/island.png" />{{ reputation.island }} {% endif %}</td>
        <td>{% if reputation.other != nil %}{{ reputation.other }} {% endif %}</td>
      </tr>
    {% endfor %}
  </tbody>
</table>
