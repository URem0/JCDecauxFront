<script>
    import { page } from '$app/stores';
	import { onMount } from 'svelte';
	import NamespaceCard from '$lib/Card.svelte';
	import Badge from '$lib/Badge.svelte';
	import Stands from '$lib/Stands.svelte';

    const contract = $page.params.contract;
    const station = $page.params.station;
    let info={};
	let pos={};

    onMount(async function () {
		const response = await fetch(`http://127.0.0.1:5000/contracts/${contract}/stations/${station}`);
		const data = await response.json();
		info = data;
		pos = data.position;
	});
</script>

<div class="px-4 text-center ">
	<p
		class="mt-2 text-3xl font-extrabold tracking-tight text-gray-800 dark:text-white"
	>
		STATION {info.name}
	</p>

	<div class="py-8 px-6 grid grid-cols-4 gap-2">
		<NamespaceCard title="Name" class="text-center col-span-2">
			<Badge status={info.status}></Badge>
		</NamespaceCard>
		<NamespaceCard title="Address" class="text-center col-span-2">
			{info.address}
		</NamespaceCard>
		<NamespaceCard title="Available Bikes" class="text-center col-span-2">
			{info.available_bikes}/{info.bike_stands}
		</NamespaceCard>
		<NamespaceCard title="See on Maps " class="text-center col-span-2">
			<a href="https://www.google.fr/maps/place/{pos.lat}+{pos.lng}">
				Open Here
			</a>
		</NamespaceCard>

		<NamespaceCard title=" " class="text-center col-span-4">
			<div class="flex flex-row items-center justify-center overflow-x-hidden space-x-1">
				{#if info.banking}
					<div>
						<Stands type="bank">
							Bank Station
						</Stands>
					</div>
				{/if}
				{#each {length: info.bike_stands} as _, i}
					{#if i <= info.available_bikes}
						<div>
							<Stands type="free">
								Bike {i+1}
							</Stands>
						</div>
					{:else}
						<div>
							<Stands>
								Bike {i+1}
							</Stands>
						</div>
					{/if}
				{/each}
			</div>
		</NamespaceCard>
	</div>
</div>