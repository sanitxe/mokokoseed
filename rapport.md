<table>
  <thead>
    <tr>
      <td>
      <td>Name
      <td>Location
      <td>Total Rapport
  </thead>
  <tbody>
    {% for npcs in site.data.npcs %}
    <tr>
      <td>
        <input type="checkbox" id="{{ npcs.id }}" value="false">
      <td> 
        {{ npcs.name }}
      <td>
        {{ npcs.loc }}
      <td>
        {{ npcs.points }}
    {% endfor %}
    </tr>
  </tbody>
</table>
