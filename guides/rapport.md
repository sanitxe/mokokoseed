---
layout: default
title: "NPC Rapport Tracker"
description: "Your Lost Ark tool for tracking rapport gained with all possible NPCs. Find their location and sort by the fastest or longest ones to farm."
---

<h1>NPC Rapport Tracker <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#totalRapport"></button></h1>

<div class="progressbar-container">
  <div class="progressbar-bar"></div>
  <div class="progressbar-label"></div>
</div>
<div class = "ready"></div>
  
<div class="modal fade" id="totalRapport" tabindex="-1" role="dialog">
  <div class="modal-dialog modal-dialog-centered" role="document">
    <div class="modal-content dark">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLongTitle">Total Rapport by Region</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body" style="columns:200px;">
{% for totalrap in site.data.totalrapport %}
<p class="break-inside: avoid;">{{ totalrap.area }}<br/>{{ totalrap.total }}</p>
{% endfor %}
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>

<table id="sortRapport" class="display dt-responsive">
  <thead>
    <tr>
      <th class="no-sort"></th>
      <th class="npc-icon-column no-sort"></th>
      <th style="width: 150px;">Name</th>
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
          {{ npcs.points | number_with_delimiter }}
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
          {% if npcs.craft != nil %}<img class="lost-icon" src="/assets/img/icon/crafting.png" /> Crafting Recipe: {{ npcs.craft }}<br />{% endif %}
          {% if npcs.sail != nil %}<img class="lost-icon" src="/assets/img/icon/icon_ship_1.png" /> Sail Glyph: {{ npcs.sail }}<br />{% endif %}
          {% if npcs.mount != nil %}Mount: {{ npcs.mount }}<br/>{% endif %}
          {% if npcs.card != nil %}<img class="lost-icon" src="/assets/img/icon/card.png" /> Card: {{ npcs.card }}<br/>{% endif %}
          {% if npcs.rune != nil %}<img class="lost-icon" src="/assets/img/icon/{{ npcs.rune | downcase }}.png" /> {{ npcs.rune | capitalize }}<br/>{% endif %}
        </td>
        <td>
          {% if npcs.giant != nil %} <img class="lost-icon" src="/assets/img/icon/giant-heart.png" /> {{ npcs.giant }} Giant Heart<br/>{% endif %}
          {% if npcs.masterpiece != nil %} <img class="lost-icon" src="/assets/img/icon/masterpiece.png" />Masterpiece {{ npcs.masterpiece }}<br/>{% endif %}
          {% if npcs.omnium != nil %} <img class="lost-icon" src="/assets/img/icon/omnium.png" /> Omnium Star {{ npcs.omnium }}<br/>{% endif %}
          {% if npcs.island != nil %}<img class="lost-icon" src="/assets/img/icon/island.png" /> {{ npcs.island }}<br/>{% endif %}
          {% if npcs.map != nil %}<img class="lost-icon" src="/assets/img/icon/map.png" /> Adventure: {{ npcs.map }}<br />{% endif %}
        </td>
        <td>
          {% if npcs.crew != nil %}<img class="lost-icon" src="/assets/img/icon/crew.png" /> Crew: {{ npcs.crew }}<br/>{% endif %}
          {% if npcs.sailor != nil %}<img class="lost-icon" src="/assets/img/icon/sailor.png" /> Sailor: {{ npcs.sailor }}<br/>{% endif %}
        </td>
      </tr>
    {% endfor %}
  </tbody>
</table>

<script>
      $(document).ready( function () {
          $('#sortRapport').dataTable( {
              searchPanes: {
                  initCollapsed: true,
                  orderable: false,
                  columns: [1],
                  panes: [
                      {
                        header: 'Location',
                        options: [
                            {
                              label: 'Rethramis',
                              value: function(rowData, rowIdx){
                                  return rowData[3].includes('Rethramis');
                              },
                            },
                            {
                            label: 'Yudia',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('Yudia');
                              },
                            },
                            {
                            label: 'West Luterra',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('West Luterra');
                              },
                            },
                            {
                            label: 'East Luterra',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('East Luterra');
                              },
                            },
                            {
                            label: 'Tortoyk',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('Tortoyk');
                              },
                            },
                            {
                            label: 'Anikka',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('Anikka');
                              },
                            },
                            {
                            label: 'Arthetine',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('Arthetine');
                              },
                            },
                            {
                            label: 'North Vern',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('North Vern');
                              },
                            },
                            {
                            label: 'Shushire',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('Shushire');
                              },
                            },
                            {
                            label: 'Rohendel',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('Rohendel');
                              },
                            },
                            {
                            label: 'Yorn',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('Yorn');
                              },
                            },
                            {
                            label: 'Feiton',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('Feiton');
                              },
                            },
                            {
                            label: 'Punika',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('Punika');
                              },
                            },
                            {
                            label: 'Island',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('Island');
                              },
                            },
                            {
                            label: 'South Vern',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('South Vern');
                              },
                            },  
                            {
                            label: 'Trixion',
                            value: function(rowData, rowIdx){
                                return rowData[3].includes('Trixion');
                              },
                            }
                          ]
                        },
                      {
                        header: 'Increase Potion',
                        options: [
                            {
                              label: 'Kindness',
                              value: function(rowData, rowIdx){
                                  return rowData[5].includes("Kindness");
                              },
                            },
                            {
                            label: 'Charisma',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes("Charisma");
                              },
                            },
                            {
                            label: 'Courage',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes("Courage");
                              },
                            },
                            {
                            label: 'Wisdom',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes("Wisdom");
                              },
                            },
                            {
                            label: 'Crit',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes("Crit");
                              },
                            },
                            {
                            label: 'Domination',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes("Domination");
                              },
                            },
                            {
                            label: 'Endurance',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes("Endurance");
                              },
                            },
                            {
                            label: 'Expertise',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes("Expertise");
                              },
                            },
                            {
                            label: 'Swiftness',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes("Swiftness");
                              },
                            },
                            {
                            label: 'Specialization',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes("Specialization");
                              },
                            },
                            {
                            label: 'Vitality',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes("Vitality");
                              },
                            },
                            {
                            label: 'Stat Increase',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes("Stat Increase");
                              },
                            },
                            {
                            label: 'Skill Point',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes("Skill Point");
                              },
                            }
                          ]
                        },
                      {
                        header: 'Reward Type',
                        options: [
                            {
                              label: 'Crafting Recipe',
                              value: function(rowData, rowIdx){
                                  return rowData[6].includes('Crafting Recipe:');
                              },
                            },
                            {
                              label: 'Card',
                              value: function(rowData, rowIdx){
                                  return rowData[6].includes('Card:');
                              },
                            },
                            {
                            label: "Rune",
                            value: function(rowData, rowIdx){
                                return rowData[6].includes("Rune:");
                              },
                            },
                            {
                            label: 'Mount',
                            value: function(rowData, rowIdx){
                                return rowData[6].includes('Mount:');
                              },
                            },
                            {
                              label: 'Sailor',
                              value: function(rowData, rowIdx){
                                  return rowData[8].includes('Sailor:');
                              },
                            },
                            {
                              label: 'Crew',
                              value: function(rowData, rowIdx){
                                  return rowData[8].includes('Crew:');
                              },
                            },
                            {
                            label: 'Sail Glyph',
                            value: function(rowData, rowIdx){
                                return rowData[6].includes("Sail Glyph:");
                              },
                            }
                          ]
                      },
                      {
                        header: 'Collectibles',
                        options: [
                            {
                              label: 'Masterpiece',
                              value: function(rowData, rowIdx){
                                  return rowData[7].includes("Masterpiece");
                              },
                            },
                            {
                            label: 'Giant Heart',
                            value: function(rowData, rowIdx){
                                return rowData[7].includes("Giant Heart");
                              },
                            },
                            {
                            label: 'Island Soul',
                            value: function(rowData, rowIdx){
                                return rowData[7].includes("Island" || "Isle");
                              },
                            },
                            {
                            label: 'Adventure Map',
                            value: function(rowData, rowIdx){
                                return rowData[7].includes("Adventure:");
                              },
                            },
                            {
                            label: 'Omnium Star',
                            value: function(rowData, rowIdx){
                                return rowData[7].includes("Omnium");
                              },
                            }
                          ]
                        }
                    ]
              },
              dom: 'Plfrtip',
              "paging": false,
              responsive: {
                  details: {
                      display: $.fn.dataTable.Responsive.display.childRowImmediate,
                      type: 'none',
                      target: ''
                  }
              },
              fixedHeader: true,
              "order": [],
              "columnDefs": [ {
                    "targets": 'no-sort',
                    "orderable": false,
              } ]
          } );
    } );  
</script>
