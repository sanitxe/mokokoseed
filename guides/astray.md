---
  title: Astray Crafting Guide
---

<h1>Astray Crafting Tracker</h1>

<div class="progress">
  <div id="astray_1" class="progress-bar" role="progressbar" style="width: 15%" aria-valuenow="15" aria-valuemin="0" aria-valuemax="100"></div>
	<div id="astray_2" class="progress-bar" role="progressbar" style="width: 15%" aria-valuenow="15" aria-valuemin="0" aria-valuemax="100"></div>
	<div id="astray_3" class="progress-bar" role="progressbar" style="width: 15%" aria-valuenow="15" aria-valuemin="0" aria-valuemax="100"></div>
	<div id="astray_4" class="progress-bar" role="progressbar" style="width: 15%" aria-valuenow="15" aria-valuemin="0" aria-valuemax="100"></div>
	<div id="astray_5" class="progress-bar" role="progressbar" style="width: 15%" aria-valuenow="15" aria-valuemin="0" aria-valuemax="100"></div>
</div>

{% for craft in site.data.astray %}
{% if craft.item != "Uncommon Ship Parts Material" %}
<div class="input-group my-3">
  <div class="input-group-prepend">
    <span class="input-group-text"><img src="/assets/img/icon/{{ craft.icon }}.png"> {{ craft.item }}</span>
  </div>  
  <input id="{{ craft.icon }}" type="text" class="form-control" aria-label="{{ craft.item }}" aria-describedby="basic-addon2">
  <div class="input-group-append">
    <span class="input-group-text" id="basic-addon2">/{{ craft.quantity }}</span>
  </div>
</div>
{% for sub in craft.method %}
<div class="input-group my-3 mx-5 sub-recipe-item">
  <div class="input-group-prepend">
    <span class="input-group-text"><img src="/assets/img/icon/{{ sub.icon }}.png"> {{ sub.recipe }}</span>
  </div>  
  <input id="{{ sub.icon }}" type="text" class="form-control" aria-label="{{ sub.recipe }}" aria-describedby="basic-addon2">
  <div class="input-group-append">
    <span class="input-group-text" id="basic-addon2">/{{ sub.quantity }}</span>
  </div>
</div>
{% endfor %}
{% endif %}
{% endfor %}

{% for craft in site.data.astray %}
{% if craft.item == "Uncommon Ship Parts Material" %}
<div class="input-group my-3">
  <div class="input-group-prepend">
    <span class="input-group-text"><img src="/assets/img/icon/{{ craft.icon }}.png"> {{ craft.item }}</span>
  </div>  
  <input id="{{ craft.icon }}" type="text" class="form-control" aria-label="{{ craft.item }}" aria-describedby="basic-addon2">
  <div class="input-group-append">
    <span class="input-group-text" id="basic-addon2">/{{ craft.quantity }}</span>
  </div>
</div>

<div class="progressbar-bar ui-progressbar ui-corner-all ui-widget ui-widget-content">
  <div id="uncommon_ship" class="ui-progressbar-value ui-corner-left ui-widget-header" role="progressbar" aria-valuenow="15" aria-valuemin="0" aria-valuemax="100"></div>
</div>

{% for sub in craft.method %}
<div class="input-group my-3 mx-5 sub-recipe-item">
  <div class="input-group-prepend">
    <span class="input-group-text"><img src="/assets/img/icon/{{ sub.icon }}.png"> {{ sub.recipe }}</span>
  </div>  
  <input id="{{ sub.icon }}" type="text" class="form-control" aria-label="{{ sub.recipe }}" aria-describedby="basic-addon2">
  <div class="input-group-append">
    <span class="input-group-text" id="basic-addon2">/{{ sub.quantity }}</span>
  </div>
</div>
{% endfor %}
{% endif %}
{% endfor %}

<script>
$( document ).ready(function() {
    $('input').each(function(){
      find = $(this).attr("id")
      found = localStorage.getItem(find)
      if (found == "NaN") {
        $(this).val('0')
      } else {
      	$(this).val(found)
      }
    })
  
  $("input").change(function() {
    $("input").each(function() {
      quantity = parseInt($(this).val())
      type = $(this).attr("id")
      localStorage.setItem(type, quantity)
    });

		strong_ore = parseInt($('#use_5_76').val())
  		if (strong_ore > 75) {strong_ore = 75}
    sturdy_timber = parseInt($('#use_4_4').val())
  		if (sturdy_timber > 75) {sturdy_timber = 75}
    heavy_iron_ore = parseInt($('#use_3_239').val())
  		if (heavy_iron_ore > 200) {heavy_iron_ore = 200}
    tender_timber = parseInt($('#use_3_253').val())
  		if (tender_timber > 200) {tender_timber = 200}

    uncommon_ship_mats = ((strong_ore + sturdy_timber + heavy_iron_ore + tender_timber)/1050)*100

    $("#uncommon_ship").attr('style','width:'+uncommon_ship_mats +"%")
  	$("#uncommon_ship").html(uncommon_ship_mats+"%")
	});
  
		strong_ore = parseInt($('#use_5_76').val())
  		if (strong_ore > 75) {strong_ore = 75}
    sturdy_timber = parseInt($('#use_4_4').val())
  		if (sturdy_timber > 75) {sturdy_timber = 75}
    heavy_iron_ore = parseInt($('#use_3_239').val())
  		if (heavy_iron_ore > 200) {heavy_iron_ore = 200}
    tender_timber = parseInt($('#use_3_253').val())
  		if (tender_timber > 200) {tender_timber = 200}

    uncommon_ship_mats = ((strong_ore + sturdy_timber + heavy_iron_ore + tender_timber)/1050)*100

    $("#uncommon_ship").attr('style','width:'+uncommon_ship_mats +"%")
  	$("#uncommon_ship").html(uncommon_ship_mats+"%")
  
  console.log(uncommon_ship_mats)
});


</script>
