---
layout: default
title: "NPC Rapport Tracker"
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
      <td></td>
      <td>Name</td>
      <td>Location</td>
      <td>Total Rapport</td>
    </tr>
  </thead>
  <tbody>
    {% for npcs in site.data.npcs %}
      <tr>
        <td>
          <input type="checkbox" id="{{ npcs.id }}" class="box">
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
