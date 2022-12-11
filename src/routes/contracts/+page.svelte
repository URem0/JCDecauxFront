<script >
	import { onMount } from 'svelte';
	import ContractsTable from '$lib/ContractsTable.svelte';
	let contracts_list = [];
	let headers = ['Name', 'Country Code', 'Commercial Name']

	onMount(async function () {
		const response = await fetch('http://127.0.0.1:5000/contracts');
		const data = await response.json();
		contracts_list = data.items
	});
</script>

<div class="mx-auto max-w-md px-4 text-center sm:max-w-3xl sm:px-6 lg:max-w-7xl lg:px-8">
	<p
		class="mt-2 text-3xl font-extrabold tracking-tight text-gray-800 dark:text-white"
	>
		LIST OF ALL CONTRACTS
	</p>

	<ContractsTable contracts_list={contracts_list} headers = {headers}></ContractsTable>
</div>
