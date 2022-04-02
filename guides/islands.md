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

<table id="sortTable">
  <thead>
    <tr>
      <th class="no-sort"></th>
      <th class="npc-icon-column no-sort"></th>
      <th>Island</th>
      <th>Method</th>
      <th>Minimum Days</th>
      <th>Compass</th>
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
            <img class="islands-icon" src="/assets/img/islands/{{ islands.icon }}" />
        </td>
        <td> 
          {{ islands.name }}
        </td>
        <td> 
          {% if islands.method = una %} Una's Daily Task {% endif %}
          {% if islands.method = quest %} Quest {% endif %}
        </td>  
        <td>
          {{ islands.days }}
        </td>
        <td>
          {{ islands.timed }}
        </td>
        <td>
          {% for notes in islands.notes %}
              
              {% if notes.startquest != nil %} <b>Starting Quest:</b> {{ notes.quest }} <br/> {% endif %}
              {% if notes.quest != nil %} <b>Quest:</b> {{ notes.quest }} <br/> {% endif %}
              {% if notes.rep != nil %} <b>Reputation:</b> {{ notes.rep }} <br/> {% endif %}
              {% if notes.achieve != nil %} <b>Achievement:</b> {{ notes.achieve }} <br/> {% endif %}
              {% if notes.coop != nil %} <b>Co-Op:</b> {{ notes.coop }} <br/> {% endif %}
              {% if notes.etc != nil %} <small>{{ notes.etc }}</small> <br/> {% endif %}
          {% endfor %}
        </td>
      </tr>
    {% endfor %}
  </tbody>
</table>
