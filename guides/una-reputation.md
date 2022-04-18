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

<table id="sortUna">
  <thead>
    <tr>
      <th class="no-sort"></th>
      <th>Reputation</th>
      <th data-toggle="tooltip" data-placement="top" title="Minimum days to acquire."><i style="font-size:30px" class="las la-calendar-day"></i></th>
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
      <tr>
        <td>
          <input type="checkbox" id="{{ reputation.id }}" class="box">
        </td>
        <td> 
          <img class="lost-icon" src="/assets/img/icon/una.png" /> {{ reputation.name }}
          <br />
          <small>{{ reputation.quests }}</small>
        </td>
        <td> 
          <span data-toggle="tooltip" data-placement="top" title="Minimum days to acquire.">{{ reputation.days }}</span>
        </td>  
        <td>
          {% if reputation.silver > 0 %}{{ reputation.silver }} <img class="lost-icon" src="/assets/img/icon/silver.png" />{% endif %}
          {% if reputation.pirate > 0 %}{{ reputation.pirate }} <img class="lost-icon" src="/assets/img/icon/pirate.png" />{% endif %}
          {% if reputation.gold > 0 %}{{ reputation.gold }} <img class="lost-icon" src="/assets/img/icon/gold.png" />{% endif %}
        </td>
        <td>{% if reputation.emote != nil %}<img class="lost-icon" src="/assets/img/icon/emote.png" /> {{ reputation.emote }}{% endif %}</td>
        <td>
          <span style="display:none">{% if reputation.silver > 0 %}silver{% endif %} {% if reputation.pirate > 0 %}pirate{% endif %} {% if reputation.gold > 0 %}gold{% endif %}</span>
          <small>
          {% if reputation.charisma == true %}<img class="lost-icon" src="/assets/img/icon/Charisma.png" /> Charisma<br />{% endif %}
          {% if reputation.wisdom == true %}<img class="lost-icon" src="/assets/img/icon/Wisdom.png" /> Wisdom<br />{% endif %}
          {% if reputation.courage == true %}<img class="lost-icon" src="/assets/img/icon/Courage.png" /> Courage<br />{% endif %}
          {% if reputation.kindness == true %}<img class="lost-icon" src="/assets/img/icon/Kindness.png" /> Kindness<br />{% endif %}
          {% if reputation.crit == true %}<img class="lost-icon" src="/assets/img/icon/Crit.png" /> Crit<br />{% endif %}
          {% if reputation.domination == true %}<img class="lost-icon" src="/assets/img/icon/Domination.png" /> Domination<br />{% endif %}
          {% if reputation.endurance == true %}<img class="lost-icon" src="/assets/img/icon/Endurance.png" /> Endurance<br />{% endif %}
          {% if reputation.expertise == true %}<img class="lost-icon" src="/assets/img/icon/Expertise.png" /> Expertise<br />{% endif %}
          {% if reputation.swiftness == true %}<img class="lost-icon" src="/assets/img/icon/Swiftness.png" /> Swiftness<br />{% endif %}
          {% if reputation.specialization == true %}<img class="lost-icon" src="/assets/img/icon/Specialization Increase.png" /> Specialization Increase<br />{% endif %}
          {% if reputation.vitality == true %}<img class="lost-icon" src="/assets/img/icon/Vitality Increase.png" /> Vitality Increase<br />{% endif %}
          {% if reputation.stat == true %}<img class="lost-icon" src="/assets/img/icon/Stat Increase.png" /> Stat Increase<br />{% endif %}
          {% if reputation.skill == true %}<img class="lost-icon" src="/assets/img/icon/Skill Point.png" /> Skill Point<br />{% endif %}
          </small>
        </td>
        <td>{% if reputation.craft != nil %}<img class="lost-icon" src="/assets/img/icon/crafting.png" /> <small>Crafting Recipe: {{ reputation.craft }}</small>{% endif %}</td>
        <td>
          {% if reputation.giant != nil %} <img class="lost-icon" src="/assets/img/icon/giant-heart.png" /> <small>{{ reputation.giant }} Giant Heart</small> {% endif %}
          {% if reputation.masterpiece != nil %} <img class="lost-icon" src="/assets/img/icon/masterpiece.png" /><small>Masterpiece {{ reputation.masterpiece }}</small> {% endif %}
          {% if reputation.omnium != nil %} <img class="lost-icon" src="/assets/img/icon/omnium.png" /> <small>Omnium Star {{ reputation.omnium }}</small> {% endif %}
        </td>
        <td>{% if reputation.mount != nil %}<small>Mount: {{ reputation.mount }}</small> {% endif %}</td>
        <td>{% if reputation.card != nil %}<img class="lost-icon" src="/assets/img/icon/card.png" /> <small>{{ reputation.card }}</small> {% endif %}</td>
        <td>{% if reputation.island != nil %}<img class="lost-icon" src="/assets/img/icon/island.png" /> <small>{{ reputation.island }}</small> {% endif %}</td>
        <td>{% if reputation.other != nil %}<small>{{ reputation.other }} </small>{% endif %}</td>
      </tr>
    {% endfor %}
  </tbody>
</table>

<script>
      $(document).ready( function () {
          $('#sortUna').dataTable( {
              searchPanes: {
                  initCollapsed: true,
                  orderable: false,
                  columns: [1],
                  panes: [
                      {
                        header: 'Coin Reward',
                        options: [
                            {
                              label: 'Silver',
                              value: function(rowData, rowIdx){
                                  return rowData[5].includes('silver');
                              },
                            },
                            {
                            label: 'Pirate Coin',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes('pirate');
                              },
                            },
                            {
                            label: 'Gold',
                            value: function(rowData, rowIdx){
                                return rowData[5].includes('gold');
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
                                  return rowData[6] != "";
                              },
                            },
                            {
                              label: 'Emote',
                              value: function(rowData, rowIdx){
                                  return rowData[4] != "";
                              },
                            },
                            {
                              label: 'Mount',
                              value: function(rowData, rowIdx){
                                  return rowData[8] != "";
                              },
                            },
                            {
                            label: 'Card',
                            value: function(rowData, rowIdx){
                                return rowData[9] != "";
                              },
                            },
                            {
                            label: 'Giant's Heart',
                            value: function(rowData, rowIdx){
                                return rowData[7].includes("Heart");
                              },
                            },
                            {
                            label: 'Masterpiece',
                            value: function(rowData, rowIdx){
                                return rowData[7].includes("Masterpiece");
                              },
                            },
                            {
                            label: 'Omnium Star',
                            value: function(rowData, rowIdx){
                                return rowData[7].includes("Omnium");
                              },
                            },
                            {
                            label: 'Island Token',
                            value: function(rowData, rowIdx){
                                return rowData[10] != "";
                              },
                            },
                            {
                              label: 'Other',
                              value: function(rowData, rowIdx){
                                  return rowData[11] != "";
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
              "order": [],
              "columnDefs": [ {
                    "targets": 'no-sort',
                    "orderable": false,
              } ]
          } );
    } );
</script>
