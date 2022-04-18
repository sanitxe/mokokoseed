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
      <th>Quests</th>
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
        </td>
        <td> 
          <span data-toggle="tooltip" data-placement="top" title="Minimum days to acquire.">{{ reputation.days }}</span>
        </td>  
        <td>
          <small>{{ reputation.quests }}</small>
        </td>
        <td>{% if reputation.silver > 0 %}{{ reputation.silver }} <img class="lost-icon" src="/assets/img/icon/silver.png" />{% endif %}
        {% if reputation.pirate > 0 %}{{ reputation.pirate }} <img class="lost-icon" src="/assets/img/icon/pirate.png" />{% endif %}</td>
        <td>{% if reputation.emote != nil %}<img class="lost-icon" src="/assets/img/icon/emote.png" /> {{ reputation.emote }}{% endif %}</td>
        <td>
          {% if reputation.stat == true %}<img class="lost-icon" src="/assets/img/icon/Stat Increase.png" /> Stat Increase<br />{% endif %}
          {% if reputation.charisma == true %}<img class="lost-icon" src="/assets/img/icon/Charisma.png" /> Charisma<br />{% endif %}
          {% if reputation.courage == true %}<img class="lost-icon" src="/assets/img/icon/Courage.png" /> Courage<br />{% endif %}
          {% if reputation.crit == true %}<img class="lost-icon" src="/assets/img/icon/Crit.png" /> Crit<br />{% endif %}
          {% if reputation.domination == true %}<img class="lost-icon" src="/assets/img/icon/Domination.png" /> Domination<br />{% endif %}
          {% if reputation.kindness == true %}<img class="lost-icon" src="/assets/img/icon/Kindness.png" /> Kindness<br />{% endif %}
          {% if reputation.specialization == true %}<img class="lost-icon" src="/assets/img/icon/Specialization Increase.png" /> Specialization Increase<br />{% endif %}
          {% if reputation.swiftness == true %}<img class="lost-icon" src="/assets/img/icon/Swiftness.png" /> Swiftness<br />{% endif %}
          {% if reputation.vitality == true %}<img class="lost-icon" src="/assets/img/icon/Vitality Increase.png" /> Vitality Increase<br />{% endif %}
          {% if reputation.wisdom == true %}<img class="lost-icon" src="/assets/img/icon/Wisdom.png" /> Wisdom<br />{% endif %}
        </td>
        <td>{% if reputation.craft != nil %}<img class="lost-icon" src="/assets/img/icon/crafting.png" /> Crafting Recipe: {{ reputation.craft }}{% endif %}</td>
        <td>{% if reputation.collect != nil %}{{ reputation.collect }} {% endif %}</td>
        <td>{% if reputation.mount != nil %}{{ reputation.mount }} {% endif %}</td>
        <td>{% if reputation.card != nil %}<img class="lost-icon" src="/assets/img/icon/card.png" /> {{ reputation.card }} {% endif %}</td>
        <td>{% if reputation.island != nil %}<img class="lost-icon" src="/assets/img/icon/island.png" /> {{ reputation.island }} {% endif %}</td>
        <td>{% if reputation.other != nil %}{{ reputation.other }} {% endif %}</td>
      </tr>
    {% endfor %}
  </tbody>
</table>

<script>
      $(document).ready( function () {
          $('#sortUna').dataTable( {
              "scrollX": true
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
</script>
