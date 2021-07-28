<script>
  export let clients;
  export let new_client

  function addCompany() {
    let client_name = document.getElementById("name").value
    clients = [...clients, {id: clients.length + 1, name: client_name}]
    new_client = !new_client
    console.log(clients)
  }
</script>
<form>
  <h2>Nuevo Cliente</h2>

  <label for="name">Nombre</label>
  <input type="text" id="name">
  <label for="rut">Rut</label>
  <input type="text" id="rut">
  <label for="contact_name">Nombre de contacto</label>
  <input type="text" id="contact_name">
  <div class="center">
    <input type="button" class="btn" value="Agregar Compañía" on:click={addCompany}>
  </div>
</form>

<style>
  .btn {
    border-radius: 8px;
  }

  .center {
    align-items: center;
    display: flex;
    justify-content: center;
  }
</style>