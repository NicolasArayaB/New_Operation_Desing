<script>
  import { Table, Button, Modal } from 'sveltestrap';
	import NewClient from './NewClient.svelte';
  import NewCustomer from './NewCustomer.svelte';

  let clients = [
    {id: 1, name: "Seleccione un Cliente"},
    {id: 2, name: "Banco Santander"},
    {id: 3, name: "Banco Internacional"},
    {id: 4, name: "Scotiabank"}
  ];

  let customers = [
    {id: 1, name: "Seleccione al solicitante"},
    {id: 2, name: "Pedro Perez"},
    {id: 3, name: "Hernan Hernandez"},
    {id: 4, name: "Fernanda Fernandez"},
    {id: 5, name: "Henrique Henriquez"}
  ];

  let sub_products = [
    {id: 1, name: "Seleccione un Sub-Producto"},
    {id: 2, name: "Inf. Soc y Poderes"},
    {id: 3, name: "P. Efectivas"}
  ];

  let products = [
    {id: 1, name: "Seleccione un Producto"},
    {id: 2, name: "Retail"},
    {id: 3, name: "Corporativo"},
    {id: 4, name: "Baja"},
    {id: 5, name: "Garantías"}
  ];

  let new_client = false;
  let new_customer = false;
  let count = 1;
  
  const toggle_cl = () => (new_client = !new_client);
  const toggle_cu = () => (new_customer = !new_customer);
</script>

<Modal body header="Nuevo Cliente" isOpen={new_client} toggle={toggle_cl}>
  <NewClient bind:clients={clients} bind:new_client={new_client} />
</Modal>

<Modal body header="Nuevo Solicitante" isOpen={new_customer} toggle={toggle_cu}>
  <NewCustomer bind:customers={customers} bind:new_customer={new_customer} />
</Modal>

<div class="new_links">
  <Button outline class="m-3" on:click={toggle_cl}>Nuevo Cliente</Button>
  <Button outline class="m-3" on:click={toggle_cu}>Nuevo Solicitante</Button>
</div>

<div class="table">
  <Table hover>
    <tr>
      <th>Cliente</th>
      <th>Solicitante</th>
      <th>Categoría</th>
      <th>Producto</th>
      <th>Sub-Producto</th>
      <th>Información adicional</th>
      <th/>
    </tr>
    
    {#each Array(count) as _, i}
      <tr>
        <td>
          <form on:submit|preventDefault={()=>count += 1} id={i}><input type="hidden" name="id" value="1" />
          <select form={i} required="required"  name="operation[company_id]" id="operation_company_id">
          {#each clients as client}
            <option value={client.id}>{client.name}</option>
          {/each}
          </select>
        </td>

        <td>
          <select form={i} required="required" name="operation[customer_id]" id="operation_customer_id" >
            {#each customers as customer}
              <option value={customer.id}>{customer.name}</option>
            {/each}
          </select>
        </td>

        <td>
          <div>
            <label for="operation_status" class="category">
              <input form={i} type="radio" name="category" value="new">
              Nueva
            </label>
            <label for="operation_status" class="category">
              <input form={i} type="radio"  name="category" value="repair">
              Reparo
            </label>
          </div>
        </td>

        <td>
          <select form={i} name="operation[product]" id="operation_product">
            {#each products as product}
              <option value={product.id}>{product.name}</option>
            {/each}
          </select>
        </td>

        <td>
          <select form={i} name="operation[sub_products]" id="operation_sub_product">
            {#each sub_products as sub_product}
              <option value={sub_products}>{sub_product.name}</option>
            {/each}
          </select>
        </td>

        <td>
          <textarea form={i} name="operation[observation]" id="operation_observation"></textarea>
        </td>

        <td>
          <Button type="submit" form={i} outline class="m-3">Crear Operación</Button>
        </td>
      </tr>
    {/each}
  </Table>
</div>

<style>
  .category {
    text-align: center;
  }

  .new_links {
    margin-top: 5em;
  }

  .table {
    background-color: #ffffff;
    border-radius: 8px;
	  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    margin: 1em auto;
    padding: 1em 1em 0 1em;
    width: min-content;
    text-align: center;
  }

</style>