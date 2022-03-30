{% for npcs in site.data.npcs %}
  <h2>{{ npcs.name }} - {{ npcs.loc }}</h2>
  <p>{{ npcs.content | markdownify }}</p>
{% endfor %}

bruhhhh
