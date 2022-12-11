<script>
    import { page } from '$app/stores';
	import { onMount } from 'svelte';
	import StationsTable from '$lib/StationsTable.svelte';

    const contract = $page.params.contract;
    const station = $page.params.station;
    let info={};
	let headers = ['Name', 'Address', 'Status'];

    onMount(async function () {
		const response = await fetch(`http://127.0.0.1:5000/contracts/${contract}/stations/${station}`);
		const data = await response.json();
		info = data
	});
</script>

{info.name}