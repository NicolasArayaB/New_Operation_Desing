<script>
	import OperationForm1 from './Components/OperationForm1.svelte'
	import OperationForm2 from './Components/OperationForm2.svelte'
	import Navbar from './Components/Navbar.svelte'

	let options = [{id: 1, status: false}, {id: 2, status: true}, {id: 3, status: false}]

</script>

<header>
	<Navbar bind:options={options}/>
</header>

<main>
	{#if options[0].status}
		<OperationForm1 />
	{:else if options[1].status}
		<OperationForm2 />		
	{:else if options[2].status}
		<!-- <OperationForm3 /> -->
		<h1>TODO</h1>
	{/if}
</main>
