<script>
	import OperationForm1 from './Components/OperationForm1.svelte';
	import OperationForm2 from './Components/OperationForm2.svelte';
	import OperationForm3 from './Components/OperationForm3.svelte';
	import Navbar from './Components/Navbar.svelte';

	let options = [{id: 1, status: true}, {id: 2, status: false}, {id: 3, status: false}];

</script>

<header>
	<Navbar bind:options={options} />
</header>

<main>
	{#if options[0].status}
		<OperationForm1 />
	{:else if options[1].status}
		<OperationForm2 />		
	{:else if options[2].status}
		<OperationForm3 />
	{/if}
</main>
