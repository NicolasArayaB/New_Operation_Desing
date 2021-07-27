<script>
  let clients = [{id: 1, name: "Seleccione un Cliente"}, {id: 2, name: "Banco Santander"}, {id: 3, name: "Banco Internacional"}, {id:4 , name: "Scotiabank"}];
  let customers = [{id:1, name:"Seleccione al solicitante"}, {id:2, name:"Pedro Perez"}, {id:3, name:"Hernan Hernandez"}, {id:4, name:"Fernanda Fernandez"}, {id:5, name:"Henrique Henriquez"}];
  let categories = [{id:1, name: "Nueva"}, {id: 2, name: "Reparo"}];
  let sub_products = [{id: 1, name:"Seleccione un Sub-Producto"}, {id: 2, name:"Inf. Soc y Poderes"}, {id: 3, name:"P. Efectivas"}]
  let products = [{id:1, name: "Seleccione un Producto"}, {id:2, name: "Retail"}, {id:3, name: "Corporativo"}, {id:4, name: "Baja"}, {id:5, name: "Garantías"}]

  let new_client = false;
  let new_customer = false;

  function addCompany() {
    let company_name = document.getElementById("name").value
    clients.push({id: clients.length + 1, name: company_name})
    new_company = !new_company
    console.log(clients)
  }

  function addCustomer() {
    let f_name = document.getElementById("first_name")
    let l_name = document.getElementById("last_name")
    let customer_name = f_name + " " + l_name
    customers.push({id: customers.length + 1, name: customer_name})
  }

</script>

<div class="form">
  <form>
    <h2>Cliente</h2>
    <select bind:value={clients} required="required" name="operation[company_id]" id="operation_company_id">
      {#each clients as client}
        <option value={client.id}>{client.name}</option>
      {/each}
    </select>
    <br>    
    <a href="#" on:click={() => new_client =! new_client}>Nuevo Cliente</a>
    
    {#if new_client}
    <h2>Nuevo Cliente</h2>
      <div class="new_form">
        <label for="name">Nombre</label>
        <input type="text" id="name">
        <label for="rut">Rut</label>
        <input type="text" id="rut">
        <label for="contact_name">Nombre de contacto</label>
        <input type="text" id="contact_name">
        <div class="center">
          <input type="button" class="btn" value="Agregar Compañía" on:click={addCompany}>
        </div>
      </div>
    {/if}

    <h2>Solicitante</h2>
    <select required="required" name="operation[customer_id]" id="operation_customer_id" bind:value={customers}>
      {#each customers as customer}
        <option value={customer.id}>{customer.name}</option>
      {/each}
    </select>
    <br>
    <a href="#" on:click={() => new_customer = !new_customer}>Nuevo Solicitante</a>

    {#if new_customer}
    <h2>Nuevo Solicitante</h2>
      <div class="new_form">
        <label for="first_name">Nombre</label>
        <input type="text" id="first_name">
        <label for="last_name">Apellido</label>
        <input type="text" id="last_name">
        <label for="rut">Rut</label>
        <input type="text" id="rut">
        <div class="center">
          <input type="button" class="btn" value="Agregar Compañía" on:click={addCustomer}>
        </div>
      </div> 
    {/if}

    <h2>Categoría</h2>
    
    {#each categories as category}
      <div class="category">
        <label for="operation_status">
          <input type="radio" bind:group={categories} name="Category" value={category.id}>
          {category.name}
        </label>
      </div>  
    {/each}

    <h2>Sub-Producto</h2>

    <select name="operation[sub_products]" id="operation_sub_product">
      {#each sub_products as sub_product}
        <option value={sub_products.id}>{sub_product.name}</option>
      {/each}
    </select>

    <h2>Producto</h2>

    <select name="operation[product]" id="operation_product">
      {#each products as product}
        <option value={product.id}>{product.name}</option>
      {/each}
    </select>

    <h2>Información adicional</h2>
    <textarea name="operation[observation]" id="operation_observation"></textarea>
    <br>
    <div class="center">
      <input type="submit" name="commit" value="Crear Operación" class="btn" data-disable-with="Create Operation">
    </div>
  </form>
</div>

<style>
  .btn {
    border-radius: 8px;
  }

  .category {
    display: inline-block;
    padding: 5px;
  }

  .center {
    align-items: center;
    display: flex;
    justify-content: center;
    margin: 10px;
  }

  .form {
    background-color: #ffffff;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    display: flex;
    justify-content: center;
		max-width: 25em;
		margin: 5em auto;
    padding: 8px;
    text-align: start;
  }

  .new_form {
    margin: 1em auto;

    justify-content: center;
		max-width: 25em;
		margin: 1em auto;
    text-align: start;
  }
</style>
