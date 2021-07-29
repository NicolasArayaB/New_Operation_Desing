<script>
  import { Button } from 'sveltestrap';

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

<div class="new_wrapper">
  <form>
    <h2>Nuevo Solicitante</h2>
    
    <label for="first_name">Nombre</label><br>
    <input type="text" id="first_name"><br>
    <label for="last_name">Apellido</label><br>
    <input type="text" id="last_name"><br>
    <label for="rut">Rut</label><br>
    <input type="text" id="rut"><br>
    <Button outline class="my-3" on:click={addCustomer}>Agregar Solicitante</Button>
  </form>
</div>
