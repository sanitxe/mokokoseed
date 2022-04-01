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

<table id="sortTable">
  <thead>
    <tr>
      <th class="no-sort"></th>
      <th class="npc-icon-column no-sort"></th>
      <th>Name</th>
      <th>Location</th>
      <th>Total Rapport</th>
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
      </tr>
    {% endfor %}
  </tbody>
</table>
