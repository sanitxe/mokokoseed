---
layout: default
title: "Island Token Tracker"
description: "Your Lost Ark tool for tracking Island Tokens. Use the table to sort by method of aquisition, and to find more information such as the minimum time required to obtain a specific Island Token."
---

<h1>Island Token Tracker</h1>

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

<table id="sortGroup">
  <thead>
    <tr>
      <th class="no-sort"></th>
      <th class="npc-icon-column no-sort"></th>
      <th>Island</th>
      <th>Method</th>
      <th data-toggle="tooltip" data-placement="top" title="Minimum days to acquire."><i style="font-size:30px" class="las la-calendar-day"></i></th>
      <th class="no-sort">Daily</th>
      <th>Notes</th>
    </tr>
  </thead>
  <tbody>
    {% for islands in site.data.islands %}
      <tr>
        <td>
          <input type="checkbox" id="{{ islands.id }}" class="box">
        </td>
        <td>
            <img class="islands-icon" src="/assets/img/islands/{{ islands.icon }}.png" />
        </td>
        <td> 
          {{ islands.name }}
        </td>
        <td> 
          {{ islands.method }}
        </td>  
        <td>
          <span data-toggle="tooltip" data-placement="top" title="Minimum days to acquire.">{{ islands.days }}</span>
        </td>
        <td>
          {% if islands.daily == true %}<i class="las la-check" data-toggle="tooltip" data-placement="top" title="Island may only appear during certain times and/or the method to obtain the token is restricted to a number of tries daily."></i>{% endif %}
          {% if islands.daily == nil %}<i class="las la-times"></i>{% endif %}
        </td>
        <td>
          {% for notes in islands.notes %}
              
              {% if notes.startquest != nil %} <img class="lost-icon" src="/assets/img/icon/quest.png"/>  <b class="startquest">Starting Quest:</b> {{ notes.startquest }} <br/> {% endif %}
              {% if notes.quest != nil %} <img class="lost-icon" src="/assets/img/icon/purplequest.png"/> <b class="quest">Quest:</b> {{ notes.quest }} <br/> {% endif %}
              {% if notes.rep != nil %} <img class="lost-icon" src="/assets/img/icon/una.png"/>  <b class="rep">Reputation:</b> {{ notes.rep }} <br/> {% endif %}
          
              {% if notes.collect != nil %} <b>Collect:</b> {{ notes.collect }} <br/> {% endif %}
              {% if notes.item != nil %} <b>Item:</b> {{ notes.item }} <br/> {% endif %} 
              {% if notes.song != nil %} <b>Song:</b> {{ notes.song }} <br/> {% endif %} 
          
              {% if notes.rapport != nil %} <img class="lost-icon" src="/assets/img/icon/rapport.png"/> <b class="rapport">Rapport:</b> {{ notes.rapport }} <br/> {% endif %}
          
              {% if notes.dungeon != nil %} <img class="lost-icon" src="/assets/img/icon/dungeon.png"/> <b class="dungeon">Dungeon:</b> {{ notes.dungeon }} <br/> {% endif %}
              {% if notes.defeat != nil %} <b>Defeat:</b> {{ notes.defeat }} <br/> {% endif %}
              {% if notes.boss != nil %} <img class="lost-icon" src="/assets/img/icon/boss.png"/> <b class="boss">Boss:</b> {{ notes.boss }} <br/> {% endif %}
          
              {% if notes.coop != nil %} <img class="lost-icon" src="/assets/img/icon/coop.png"/> <b class="coop">Co-Op:</b> {{ notes.coop }} <br/> {% endif %}
              {% if notes.etc != nil %} <small>{{ notes.etc }}</small> <br/> {% endif %}
          {% endfor %}
        </td>
      </tr>
    {% endfor %}
  </tbody>
</table>
