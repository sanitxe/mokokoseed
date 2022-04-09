---
  title: Astray Crafting Guide
---

<h1>Astray Crafting Tracker</h1>

<div class="progress">
  <div id="astray_1" class="progress-bar" role="progressbar"></div>
	<div id="astray_2" class="progress-bar" role="progressbar"></div>
	<div id="astray_3" class="progress-bar" role="progressbar"></div>
	<div id="astray_4" class="progress-bar" role="progressbar"></div>
	<div id="astray_5" class="progress-bar" role="progressbar"></div>
</div>

<div class="row">
	<div class="col-lg-8">
{% for craft in site.data.astray %}
{% if craft.item != "Uncommon Ship Parts Material" %}
<div class="input-group my-3">
  <div class="input-group-prepend">
    <span class="input-group-text {{ craft.color }}"><img src="/assets/img/icon/{{ craft.icon }}.png"> {{ craft.item }}</span>
  </div>  
  <input id="{{ craft.icon }}" type="text" class="form-control" aria-label="{{ craft.item }}" aria-describedby="basic-addon2">
  <div class="input-group-append">
    <span class="input-group-text {{ craft.color }}" id="basic-addon2">/{{ craft.quantity }}</span>
  </div>
</div>
{% for sub in craft.method %}
<div class="input-group my-3 mx-5 sub-recipe-item">
  <div class="input-group-prepend">
    <span class="input-group-text {{ sub.color }}"><img src="/assets/img/icon/{{ sub.icon }}.png"> {{ sub.recipe }}</span>
  </div>  
  <input id="{{ sub.icon }}" type="text" class="form-control" aria-label="{{ sub.recipe }}" aria-describedby="basic-addon2">
  <div class="input-group-append">
    <span class="input-group-text {{ sub.color }}" id="basic-addon2">/{{ sub.quantity }}</span>
  </div>
</div>
{% endfor %}
{% endif %}
{% endfor %}

{% for craft in site.data.astray %}
{% if craft.item == "Uncommon Ship Parts Material" %}
<div class="input-group my-3">
  <div class="input-group-prepend">
    <span class="input-group-text {{ craft.color }}"><img src="/assets/img/icon/{{ craft.icon }}.png"> {{ craft.item }}</span>
  </div>  
  <input id="{{ craft.icon }}" type="text" class="form-control" aria-label="{{ craft.item }}" aria-describedby="basic-addon2">
  <div class="input-group-append">
    <span class="input-group-text {{ craft.color }}" id="basic-addon2">/{{ craft.quantity }}</span>
  </div>
</div>

<div class="my-3 mx-5 progress">
  <div id="uncommon_ship" class="progress-bar" role="progressbar"></div>
</div>

{% for sub in craft.method %}
<div class="input-group my-3 mx-5 sub-recipe-item">
  <div class="input-group-prepend">
    <span class="input-group-text {{ sub.color }}"><img src="/assets/img/icon/{{ sub.icon }}.png"> {{ sub.recipe }}</span>
  </div>  
  <input id="{{ sub.icon }}" type="text" class="form-control" aria-label="{{ sub.recipe }}" aria-describedby="basic-addon2">
  <div class="input-group-append">
    <span class="input-group-text {{ sub.color }}" id="basic-addon2">/{{ sub.quantity }}</span>
  </div>
</div>
{% endfor %}
{% endif %}
{% endfor %}
</div>

<div class="col-sm">
  <h2>Progress: <span id="progress"></span></h2>
</div>
  
</div>
<script>
$(document).ready(function() {

  /*Reset all fields to 0 at first load*/
  $('input').each(function() {
    find = $(this).attr("id")
    found = localStorage.getItem(find)
    if (found == "NaN" || found == undefined) {
      $(this).val('0')
    } else {
      $(this).val(found)
    }
  })

  /*When fields have been altered LOCALSTORAGE*/
  $("input").change(function() {
    $("input").each(function() {
      check = $(this).val()
      if (check == "" || check == undefined) {
        $(this).val('0')
      }
      quantity = parseInt($(this).val())
      type = $(this).attr("id")
      localStorage.setItem(type, quantity)
    });
    
  /*When fields have been altered CALCULATIONS*/
  astray_blueprint = parseInt($('#use_5_76').val())
  if (astray_blueprint > 1) {
    astray_blueprint = 1
  }
  she_drifts = parseInt($('#icon_quest_16_shedrifts').val())
  if (she_drifts > 25) {
    she_drifts = 25
  }
  astray_manual = parseInt($('#all_quest_03_5').val())
  if (astray_manual > 1) {
    astray_manual = 1
  }
  pirate_star = parseInt($('#all_quest_02_58').val())
  if (pirate_star > 1) {
    pirate_star = 1
  }
  cert_pirate = parseInt($('#use_4_76').val())
  if (cert_pirate > 1) {
    cert_pirate = 1
  }
  pest = parseInt($('#icon_quest_16_pest').val())
  if (pest > 15) {
    pest = 15
  }
  wood = parseInt($('#use_3_252').val())
  if (wood > 570) {
    wood = 570
  }
  uncommon_parts = parseInt($('#use_8_118').val())
  if (uncommon_parts > 15) {
    uncommon_parts = 15
  }
  strong_ore = parseInt($('#use_5_76').val())
  if (strong_ore > 75) {
    strong_ore = 75
  }
  sturdy_timber = parseInt($('#use_4_4').val())
  if (sturdy_timber > 75) {
    sturdy_timber = 75
  }
  heavy_iron_ore = parseInt($('#use_3_239').val())
  if (heavy_iron_ore > 200) {
    heavy_iron_ore = 200
  }
  tender_timber = parseInt($('#use_3_253').val())
  if (tender_timber > 200) {
    tender_timber = 200
  }
  gold = parseInt($('#use_2_108').val())
  if (gold > 500) {
    gold = 500
  }

  /*Calculate Astray completion*/
  astray_1 = (((astray_blueprint + she_drifts) / 26) * 100) / 5
  $("#astray_1").attr('style', 'width:' + astray_1 + "%")
  astray_2 = (((astray_manual + pirate_star) / 2) * 100) / 5
  $("#astray_2").attr('style', 'width:' + astray_2 + "%")
  astray_3 = (((cert_pirate + pest) / 16) * 100) / 5
  $("#astray_3").attr('style', 'width:' + astray_3 + "%")
  astray_4 = ((wood / 570) * 100) / 5
  $("#astray_4").attr('style', 'width:' + astray_4 + "%")
  astray_5 = ((uncommon_parts / 15) * 100) / 5
  $("#astray_5").attr('style', 'width:' + astray_5 + "%")

  astray_percent = astray_1 + astray_2 + astray_3 + astray_4 + astray_5
  $("#progress").html(Math.round(astray_percent) + "%")



  /*Calculate completion of Uncommon Ship Parts Material*/
  uncommon_ship_mats = ((strong_ore + sturdy_timber + heavy_iron_ore + tender_timber + gold) / 1050) * 100

  $("#uncommon_ship").attr('style', 'width:' + uncommon_ship_mats + "%")
  $("#uncommon_ship").html(Math.round(uncommon_ship_mats) + "%")
  });

  /*First iteration*/
  astray_blueprint = parseInt($('#use_5_76').val())
  if (astray_blueprint > 1) {
    astray_blueprint = 1
  }
  she_drifts = parseInt($('#icon_quest_16_shedrifts').val())
  if (she_drifts > 25) {
    she_drifts = 25
  }
  astray_manual = parseInt($('#all_quest_03_5').val())
  if (astray_manual > 1) {
    astray_manual = 1
  }
  pirate_star = parseInt($('#all_quest_02_58').val())
  if (pirate_star > 1) {
    pirate_star = 1
  }
  cert_pirate = parseInt($('#use_4_76').val())
  if (cert_pirate > 1) {
    cert_pirate = 1
  }
  pest = parseInt($('#icon_quest_16_pest').val())
  if (pest > 15) {
    pest = 15
  }
  wood = parseInt($('#use_3_252').val())
  if (wood > 570) {
    wood = 570
  }
  uncommon_parts = parseInt($('#use_8_118').val())
  if (uncommon_parts > 15) {
    uncommon_parts = 15
  }
  strong_ore = parseInt($('#use_5_76').val())
  if (strong_ore > 75) {
    strong_ore = 75
  }
  sturdy_timber = parseInt($('#use_4_4').val())
  if (sturdy_timber > 75) {
    sturdy_timber = 75
  }
  heavy_iron_ore = parseInt($('#use_3_239').val())
  if (heavy_iron_ore > 200) {
    heavy_iron_ore = 200
  }
  tender_timber = parseInt($('#use_3_253').val())
  if (tender_timber > 200) {
    tender_timber = 200
  }
  gold = parseInt($('#use_2_108').val())
  if (gold > 500) {
    gold = 500
  }

  /*Calculate Astray completion*/
  astray_1 = (((astray_blueprint + she_drifts) / 26) * 100) / 5
  $("#astray_1").attr('style', 'width:' + astray_1 + "%")
  astray_2 = (((astray_manual + pirate_star) / 2) * 100) / 5
  $("#astray_2").attr('style', 'width:' + astray_2 + "%")
  astray_3 = (((cert_pirate + pest) / 16) * 100) / 5
  $("#astray_3").attr('style', 'width:' + astray_3 + "%")
  astray_4 = ((wood / 570) * 100) / 5
  $("#astray_4").attr('style', 'width:' + astray_4 + "%")
  astray_5 = ((uncommon_parts / 15) * 100) / 5
  $("#astray_5").attr('style', 'width:' + astray_5 + "%")

  astray_percent = astray_1 + astray_2 + astray_3 + astray_4 + astray_5
  $("#progress").html(Math.round(astray_percent) + "%")



  /*Calculate completion of Uncommon Ship Parts Material*/
  uncommon_ship_mats = ((strong_ore + sturdy_timber + heavy_iron_ore + tender_timber + gold) / 1050) * 100

  $("#uncommon_ship").attr('style', 'width:' + uncommon_ship_mats + "%")
  $("#uncommon_ship").html(Math.round(uncommon_ship_mats) + "%")
});
</script>
