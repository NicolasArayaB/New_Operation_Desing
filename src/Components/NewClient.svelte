<script>
  import { Button } from 'sveltestrap';
  export let clients;
  export let new_client

  function addCompany() {
    let client_name = document.getElementById("name").value
    clients = [...clients, {id: clients.length + 1, name: client_name}]
    new_client = !new_client
    console.log(clients)
  }
</script>

<div class="new_wrapper">
  <form>
    <h2>Nuevo Cliente</h2>

    <label for="name">Nombre</label><br>
    <input type="text" id="name"><br>
    <label for="rut">Rut</label><br>
    <input type="text" id="rut"><br>
    <label for="contact_name">Nombre de contacto</label><br>
    <input type="text" id="contact_name"><br>
    <Button outline class="my-3" on:click={addCompany}>Agregar Cliente</Button>
  </form>
</div>
