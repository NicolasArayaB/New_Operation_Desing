<script>
	import OperationForm1 from './Components/OperationForm1.svelte'
	import Navbar from './Components/Navbar.svelte'

	let options = [{id: 1, status: true}, {id: 2, status: false}, {id: 3, status: false}]
</script>

<header>
	<Navbar bind:options={options}/>
</header>

<main>
	{#if options[0].status}
		<OperationForm1 />
	{/if}

	{#if options[1].status}
		<!-- <OperationForm2 /> -->
		<h1>TODO</h1>
	{/if}
	{#if options[2].status}
		<!-- <OperationForm3 /> -->
		<h1>TODO</h1>
	{/if}
</main>
