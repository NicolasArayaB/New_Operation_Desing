<script>
  import { Button, Modal, Container, Row, Col } from 'sveltestrap';
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

<div class="mt-5 fixed-top">
  <div class="title">
    <h1>Opción 3</h1>
  </div>
  <Button outline class="m-3" on:click={toggle_cl}>Nuevo Cliente</Button>
  <Button outline class="m-3" on:click={toggle_cu}>Nuevo Solicitante</Button>
</div>

<Container>
  <Row class="d-flex flex-nowrap mt-5">
    {#each Array(count) as _, i}
    <Col>
      <div class="wrapper mx-auto">
        <form id="form1" on:submit|preventDefault={()=>count += 1}>
          <h2>Cliente</h2>
        
          <select required="required" name="operation[company_id]" id="operation_company_id">
            {#each clients as client}
              <option value={client.id}>{client.name}</option>
            {/each}
          </select>
          <br>    
        
          <h2>Solicitante</h2>

          <select required="required" name="operation[customer_id]" id="operation_customer_id">
            {#each customers as customer}
              <option value={customer.id}>{customer.name}</option>
            {/each}
          </select>
          <br>
        
          <h2>Categoría</h2>
          <div>
            <label for="operation_status" class="category">
              <input type="radio" name="category" value="new">
              Nueva
            </label>
            <label for="operation_status" class="category">
              <input type="radio"  name="category" value="repair">
              Reparo
            </label>
          </div>  
        
          <h2>Producto</h2>
        
          <select name="operation[product]" id="operation_product">
            {#each products as product}
              <option value={product.id}>{product.name}</option>
            {/each}
          </select>
        
          <h2>Sub-Producto</h2>
        
          <select name="operation[sub_products]" id="operation_sub_product">
            {#each sub_products as sub_product}
              <option value={sub_products.id}>{sub_product.name}</option>
            {/each}
          </select>
        
          <h2>Información adicional</h2>
          <textarea name="operation[observation]" id="operation_observation"></textarea>
          <br>
        
          <div class="center">
            <Button outline class="my-3">Crear Operación</Button>
          </div>
         </form>
      </div>
    </Col>
    {/each}
  </Row>
</Container>

<style>
  .category {
    display: inline-block;
    padding: 5px;
  }

  .title {
    margin-top: 2em;
  }

  .wrapper {
	  background-color: #ffffff;
	  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
	  display: flex;
	  justify-content: center;
    margin-top: 12em;
	  max-width: 25em;
	  min-width: 22em;
	  padding: 8px;
	  text-align: start;
  }
</style>
