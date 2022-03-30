---
layout: default
title: NPC Rapport Tracker
---

<table>
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
          <input type="checkbox" id="{{ npcs.id }}" class="box"></input>
        </td>
        <td> 
          {{ npcs.name }}
        </td>        
        <td>
          {{ npcs.loc }}
        </td>
        <td>
          {{ npcs.points }}
      </tr>
    {% endfor %}
  </tbody>
</table>
