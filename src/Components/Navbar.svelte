<script>
  export let options;
</script>

<div class="nav-bar">
  <a href="#1" on:click={() => options = [{id: 1, status: true}, {id:2, status:false}, {id: 3, status: false}]}>Opción 1</a>
  <a href="#2" on:click={() => options = [{id: 1, status: false}, {id:2, status:true}, {id: 3, status: false}]}>Opción 2</a>
  <a href="#3" on:click={() => options = [{id: 1, status: false}, {id:2, status:false}, {id: 3, status: true}]}>Opción 3</a>
</div>

<style>
  .nav-bar {
    background-color: rgb(30, 39, 56);
    height: 3rem;
    line-height: 3rem;
    left: 0px;
    position: fixed;
    top: 0px;
    width: 100%;
  }

  .nav-bar a {
    color: #ffffff;
    margin: 5rem;
    text-decoration: none;
  }
</style>