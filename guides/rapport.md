---
layout: default
title: MOKOKO SEED | NPC Rapport Tracker
---

<h1>NPC Rapport Tracker</h1>
<i>Work in progress.</i>

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
