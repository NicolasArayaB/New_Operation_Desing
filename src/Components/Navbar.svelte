<script>
  export let options;
</script>

<div class="navbar">
  <a href="#" on:click={() => options = [{id: 1, status: true}, {id:2, status:false}, {id: 3, status: false}]}>Opción 1</a>
  <a href="#" on:click={() => options = [{id: 1, status: false}, {id:2, status:true}, {id: 3, status: false}]}>Opción 2</a>
  <a href="#" on:click={() => options = [{id: 1, status: false}, {id:2, status:false}, {id: 3, status: true}]}>Opción 3</a>
</div>

<style>
  .navbar {
    background-color: rgb(30, 39, 56);
    height: 3rem;
    line-height: 3rem;
    left: 0px;
    position: fixed;
    top: 0px;
    width: 100%;
  }

  .navbar a {
    color: #ffffff;
    margin: 5rem;
    text-decoration: none;
  }
</style>