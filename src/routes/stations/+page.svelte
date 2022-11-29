<script >
	import { onMount } from 'svelte';
	let stations_list = [];

	onMount(async function () {
		const response = await fetch('http://127.0.0.1:5000/stations');
		const data = await response.json();
		stations_list = data.items
	});
</script>

<div class="mx-auto max-w-md px-4 text-center sm:max-w-3xl sm:px-6 lg:max-w-7xl lg:px-8">
	<p
		class="mt-2 text-3xl font-extrabold tracking-tight text-gray-800 dark:text-white"
	>
		LIST OF ALL STATIONS
	</p>

	<div class="py-4 flex flex-col">
		<div class="-m-1.5 overflow-x-auto">
		  <div class="p-1.5 min-w-full inline-block align-middle">
			<div class="border rounded-lg overflow-hidden dark:border-gray-700">
					<table class="min-w-full text-sm text-left text-gray-500 dark:text-gray-400 shadow-md rounded-sm">
						<thead class="text-xs text-gray-700 uppercase bg-gray-100">
							<tr>
								<th scope="col" class="py-2 px-4">Name</th>
								<th scope="col" class="py-2 px-4">Address</th>
								<th scope="col" class="py-2 px-4">Status</th>
							</tr>
						</thead>
						<tbody>
							{#each stations_list as stations}
							<tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700">
								<td class="py-2 px-4">{stations.name}</td>
								<td class="py-2 px-4">{stations.address}</td>
								<td class="py-2 px-4">{stations.status}</td>
							</tr>
							{/each}
						</tbody>
					</table>
				</div>
			</div>
		</div>
	</div>
</div>