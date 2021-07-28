<script>
  export let customers;
  export let new_customer;
  
  function addCustomer() {
    let f_name = document.getElementById("first_name");
    let l_name = document.getElementById("last_name");
    let customer_name = f_name + " " + l_name;
    customers = [...customers, {id: customers.length + 1, name: customer_name}];
    new_customer = !new_customer;
  }
</script>

<form>
  <h2>Nuevo Solicitante</h2>
  
  <label for="first_name">Nombre</label>
  <input type="text" id="first_name">
  <label for="last_name">Apellido</label>
  <input type="text" id="last_name">
  <label for="rut">Rut</label>
  <input type="text" id="rut">
  <div class="center">
    <input type="button" class="btn" value="Agregar Compañía" on:click={addCustomer}>
  </div>
</form>