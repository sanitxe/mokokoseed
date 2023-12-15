---
layout: default
title: "Lost Ark Character Select Backgrounds"
description: "A collection of Lost Ark's Character Selection backgrounds."
---

<h1>Character Select Backgrounds</h1>

<div class="card-deck">

{% for bg in site.data.wallpaper %}
  <div class="col-lg-3 mb-3">
  <div class="card h-100">
    <a href="/assets/img/wallpaper/large/wallpaper_icon_{{ bg.icon }}.png" data-toggle="lightbox" {% if bg.footer != nil %}data-footer="Source: {{ bg.footer }}"{% endif %}><img class="card-img-top img-fluid" src="/assets/img/wallpaper/wallpaper_icon_{{ bg.mini }}.png"></a>
    <div class="card-body">
      <h5 class="card-title">{{ bg.title }}</h5>
      <p class="card-text">{{ bg.desc }}</p>
      <p class="card-text">{{ bg.obtain }}</p>
    </div>
  </div>
  </div>
{% endfor %}

</div>


<script>
  $(document).on('click', '[data-toggle="lightbox"]', function(event) {
                event.preventDefault();
                $(this).ekkoLightbox();
            });
</script>
