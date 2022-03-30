<table>
  <thead>
    <tr>
      <td></td>
      <td>Name</td>
      <td>Location</td>
      <td>Total Rapport</td>
    </tr>
  </thead>
  <tbody>
    {% for npcs in site.data.npcs %}
      <tr>
        <td>
          <input type="checkbox" id="{{ npcs.id }}" class="box"></input>
        </td>
        <td> 
          {{ npcs.name }}
        </td>        
        <td>
          {{ npcs.loc }}
        </td>
        <td>
          {{ npcs.points }}
      </tr>
    {% endfor %}
  </tbody>
</table>

<script>
 window.onload = function() {
  let boxes = document.getElementsByClassName('box').length;

  function save() {	
    for(let i = 1; i <= boxes; i++){
      var checkbox = document.getElementById(String(i));
      localStorage.setItem("checkbox" + String(i), checkbox.checked);	
    }
  }

  //for loading
  for(let i = 1; i <= boxes; i++){
    if(localStorage.length > 0){
      var checked = JSON.parse(localStorage.getItem("checkbox" + String(i)));
      document.getElementById(String(i)).checked = checked;
    }
  }
  window.addEventListener('change', save);
  };
</script>
