<script>
    import { page } from '$app/stores';
	import { onMount } from 'svelte';
	import StationsTable from '$lib/StationsTable.svelte';

    const contract = $page.params.contract;
    let stations_list = [];
	let headers = ['Name', 'Address', 'Status'];
    onMount(async function () {
		const response = await fetch(`http://127.0.0.1:5000/contracts/${contract}/stations`);
		const data = await response.json();
		stations_list = data.items
	});
</script>

<div class="mx-auto max-w-md px-4 text-center sm:max-w-3xl sm:px-6 lg:max-w-7xl lg:px-8">
	<p
		class="mt-2 text-3xl font-extrabold tracking-tight text-gray-800 dark:text-white"
	>
		LIST OF {contract.toUpperCase()}'S STATIONS
	</p>
	<StationsTable stations_list={stations_list} headers={headers}></StationsTable>
</div>