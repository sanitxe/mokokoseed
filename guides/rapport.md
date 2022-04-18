---
layout: default
title: "NPC Rapport Tracker"
description: "Your Lost Ark tool for tracking rapport gained with all possible NPCs. Find their location and sort by the fastest or longest ones to farm."
---

<h1>NPC Rapport Tracker</h1>

<div class="progressbar-container">
  <div class="progressbar-bar"></div>
  <div class="progressbar-label"></div>
</div>
<div class = "ready"></div>

<div class="alert alert-danger" role="alert">
  This is currently a <strong>work in progress</strong>. Progression is currently stored locally only. Clearing your browser's localStorage will reset the table.
</div>

<div class="alert alert-info" role="alert">
  PROTIP: You can sort multiple categories by pressing SHIFT + Left Click on the table headers.
</div>

<table id="sortTable" class="display dt-responsive nowrap">
  <thead>
    <tr>
      <th class="no-sort"></th>
      <th class="npc-icon-column no-sort"></th>
      <th>Name</th>
      <th>Location</th>
      <th>Total Rapport</th>
      <th>Potion</th>
      <th>Unlock</th>
      <th>Collection</th>
      <th>Hire</th>
    </tr>
  </thead>
  <tbody>
    {% for npcs in site.data.npcs %}
      <tr>
        <td>
          <input type="checkbox" id="{{ npcs.id }}" class="box">
        </td>
        <td>
            <img class="npc-icon" src="/assets/img/npc/{{ npcs.icon }}" />
        </td>
        <td> 
          {{ npcs.name }}
        </td>        
        <td>
          {{ npcs.loc }}
        </td>
        <td>
          {{ npcs.points }}
        </td>
        <td>
          {% if npcs.charisma == true %}<img class="lost-icon" src="/assets/img/icon/Charisma.png" /> Charisma<br />{% endif %}
          {% if npcs.wisdom == true %}<img class="lost-icon" src="/assets/img/icon/Wisdom.png" /> Wisdom<br />{% endif %}
          {% if npcs.courage == true %}<img class="lost-icon" src="/assets/img/icon/Courage.png" /> Courage<br />{% endif %}
          {% if npcs.kindness == true %}<img class="lost-icon" src="/assets/img/icon/Kindness.png" /> Kindness<br />{% endif %}
          {% if npcs.crit == true %}<img class="lost-icon" src="/assets/img/icon/Crit.png" /> Crit<br />{% endif %}
          {% if npcs.domination == true %}<img class="lost-icon" src="/assets/img/icon/Domination.png" /> Domination<br />{% endif %}
          {% if npcs.endurance == true %}<img class="lost-icon" src="/assets/img/icon/Endurance.png" /> Endurance<br />{% endif %}
          {% if npcs.expertise == true %}<img class="lost-icon" src="/assets/img/icon/Expertise.png" /> Expertise<br />{% endif %}
          {% if npcs.swiftness == true %}<img class="lost-icon" src="/assets/img/icon/Swiftness.png" /> Swiftness<br />{% endif %}
          {% if npcs.specialization == true %}<img class="lost-icon" src="/assets/img/icon/Specialization Increase.png" /> Specialization<br />{% endif %}
          {% if npcs.vitality == true %}<img class="lost-icon" src="/assets/img/icon/Vitality Increase.png" /> Vitality<br />{% endif %}
          {% if npcs.greater-vitality == true %}<img class="lost-icon" src="/assets/img/icon/Greater Vitality.png" /> Greater Vitality<br />{% endif %}
          {% if npcs.stat == true %}<img class="lost-icon" src="/assets/img/icon/Stat Increase.png" /> Stat Increase<br />{% endif %}
          {% if npcs.greater-stat == true %}<img class="lost-icon" src="/assets/img/icon/Greater Stat Increase.png" /> Greater Stat<br />{% endif %}
          {% if npcs.skill == true %}<img class="lost-icon" src="/assets/img/icon/Skill Point.png" /> Skill Point<br />{% endif %}
        </td>
        <td>
          {% if npcs.craft != nil %}<img class="lost-icon" src="/assets/img/icon/crafting.png" /> {{ npcs.craft }}<br />{% endif %}
          {% if npcs.map != nil %}<img class="lost-icon" src="/assets/img/icon/map.png" /> Adventure: {{ npcs.map }}<br />{% endif %}
          {% if npcs.sail != nil %}<img class="lost-icon" src="/assets/img/icon/icon_ship_1.png" /> Sail Glyph: {{ npcs.sail }}<br />{% endif %}
          {% if npcs.mount != nil %}Mount: {{ npcs.mount }}<br/>{% endif %}
          {% if npcs.card != nil %}<img class="lost-icon" src="/assets/img/icon/card.png" /> {{ npcs.card }}<br/>{% endif %}
        </td>
        <td>
          {% if npcs.giant != nil %} <img class="lost-icon" src="/assets/img/icon/giant-heart.png" /> {{ npcs.giant }} Giant Heart<br/>{% endif %}
          {% if npcs.masterpiece != nil %} <img class="lost-icon" src="/assets/img/icon/masterpiece.png" />Masterpiece {{ npcs.masterpiece }}<br/>{% endif %}
          {% if npcs.omnium != nil %} <img class="lost-icon" src="/assets/img/icon/omnium.png" /> Omnium Star {{ npcs.omnium }}<br/>{% endif %}
          {% if npcs.island != nil %}<img class="lost-icon" src="/assets/img/icon/island.png" /> {{ npcs.island }}<br/>{% endif %}
        </td>
        <td>
          {% if npcs.crew != nil %}<img class="lost-icon" src="/assets/img/icon/crew.png" /> Crew: {{ npcs.crew }}<br/>{% endif %}
          {% if npcs.sailor != nil %}<img class="lost-icon" src="/assets/img/icon/sailor.png" /> Sailor: {{ npcs.sailor }}<br/>{% endif %}
        </td>
      </tr>
    {% endfor %}
  </tbody>
</table>
