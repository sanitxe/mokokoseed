---
layout: default
title: "Sea Bounties Tracker"
description: "Your Lost Ark tool for tracking Lost Ark's Sea Bounties."
---

<h1>Sea Bounties Tracker <button type="button" style="margin-top:0" class="btn btn-dark" data-toggle="modal" data-target="#totalRapport">Total Rapport for Tokens</button></h1>

<div class="progressbar-container">
  <div class="progressbar-bar"></div>
  <div class="progressbar-label"></div>
</div>
<div class = "ready"></div>

<table id="sortBounty" class="display dt-responsive">
  <thead>
    <tr>
      <th class="no-sort"></th>
      <th class="npc-icon-column no-sort"></th>
      <th style="width: 150px;">Name</th>
      <th>Method</th>
      <th>Location</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    {% for map in site.data.bounty %}
      <tr>
        <td>
          <input type="checkbox" id="{{ map.id }}" class="box">
        </td>
        <td>
            <img class="map-icon" src="/assets/img/bounty/{{ map.icon }}" />
        </td>
        <td> 
          {{ map.name }}
        </td>        
        <td>
          {{ map.method }}
        </td>
        <td>
          {{ map.loc }}
        </td>
        <td>
          {% if map.tome != nil %}<b>Adventurer's Tome:</b> {{ map.tome }}<br />{% endif %}
          {% if map.stronghold != nil %}<b>Stronghold Merchant:</b> {{ map.stronghold }}<br />{% endif %}
          {% if map.advent != nil %}<img class="lost-icon" src="/assets/img/icon/a_seal.png" />Adventurer's Seal x{{ map.advent }}<br />{% endif %}
          {% if map.victory != nil %}<img class="lost-icon" src="/assets/img/icon/v_seal.png" />Victory Seal x{{ map.victory }}<br />{% endif %}
          {% if map.raid != nil %}<img class="lost-icon" src="/assets/img/icon/r_seal.png" />Raid Seal x{{ map.raid }}<br />{% endif %}
          {% if map.rapport != nil %}<img class="lost-icon" src="/assets/img/icon/rapport.png" /> <b class="rapport">Rapport:</b> {{ map.rapport }}<br />{% endif %}
          {% if map.spearfish != nil %}<img class="lost-icon" src="/assets/img/icon/vessel.png" /> <b>Spearfish Hunting Guild Vessel:</b> {{ map.spearfish }}<br />{% endif %}
          {% if map.arc != nil %}<img class="lost-icon" src="/assets/img/icon/arc_coin.png" /> Arcturus's Coin x{{ map.arc }}<br />{% endif %}
          {% if map.gie != nil %}<img class="lost-icon" src="/assets/img/icon/gie_coin.png" /> Gienah's Coin x{{ map.gie }}<br />{% endif %}
          {% if map.shipwreck == true %}<img class="lost-icon" src="/assets/img/icon/ship.png" /> <b>Shipwreck</b> <br />{% endif %}
          {% if map.soul != nil %}<img class="lost-icon" src="/assets/img/icon/adventureisland.png" /> <b class="island">Island:</b> {{ map.soul }}<br />{% endif %}
          {% if map.boss != nil %}<img class="lost-icon" src="/assets/img/icon/boss.png" /> <b class="boss">Boss:</b> {{ map.boss }}<br />{% endif %}
          {% if map.island != nil %}<img class="lost-icon" src="/assets/img/icon/boss.png" /> {{ map.collectible }}<br />{% endif %}
          {% if map.una != nil %}<img class="lost-icon" src="/assets/img/icon/una.png" /> <b class="rep">Reputation:</b> {{ map.una }}<br />{% endif %}
          {% if map.quest != nil %}<img class="lost-icon" src="/assets/img/icon/purplequest.png" /> <b class="quest">Quest:</b> {{ map.quest }}<br />{% endif %}
        </td>
      </tr>
    {% endfor %}
  </tbody>
</table>

<script>
      $(document).ready( function () {
          var groupColumn = 3;
          var table = $('#sortBounty').DataTable({
            "paging": false,
            responsive: {
                  details: {
                      display: $.fn.dataTable.Responsive.display.childRowImmediate,
                      type: 'none',
                      target: ''
                  }
              },
            "columnDefs": [
                  { "visible": false, "targets": groupColumn },
                  { "targets": 'no-sort', "orderable": false }
              ],
              "order": [[ groupColumn, 'asc' ]],
              "displayLength": 25,
              "drawCallback": function ( settings ) {
                  var api = this.api();
                  var rows = api.rows( {page:'current'} ).nodes();
                  var last=null;

                  api.column(groupColumn, {page:'current'} ).data().each( function ( group, i ) {
                      if ( last !== group ) {
                          $(rows).eq( i ).before(
                              '<tr class="group"><td colspan="6">'+group+'</td></tr>'
                          );

                          last = group;
                      }
                  } );
              }
          } );

          // Order by the grouping
          $('#sortBounty tbody').on( 'click', 'tr.group', function () {
              var currentOrder = table.order()[0];
              if ( currentOrder[0] === groupColumn && currentOrder[1] === 'asc' ) {
                  table.order( [ groupColumn, 'desc' ] ).draw();
              }
              else {
                  table.order( [ groupColumn, 'asc' ] ).draw();
              }
          } );
    } );  
</script>
