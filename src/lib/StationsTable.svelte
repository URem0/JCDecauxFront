<script>
    export let stations_list
	let headers = ['Status', 'Name', 'Bikes Available', 'Filling', 'Address',];

    import Badge from "./Badge.svelte";
</script>

{#if !stations_list.length}
    <p class="mx-auto mt-5 max-w-prose text-lg text-black-400">
        No Stations
    </p>
{:else}
    <div class="py-4 flex flex-col">
        <div class="-m-1.5 overflow-x-auto">
        <div class="p-1.5 min-w-full inline-block align-middle">
            <div class="border rounded-lg overflow-hidden dark:border-gray-700">
                    <table class="min-w-full text-sm text-left text-gray-500 dark:text-gray-400 shadow-md rounded-sm">
                        <thead class="text-xs text-gray-700 uppercase bg-gray-100">
                            <tr>
                                {#each headers as header}
                                    <th scope="col" class="py-2 px-4">{header}</th>
                                {/each}
                            </tr>
                        </thead>
                        <tbody>
                            {#each stations_list as station}
                            <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700">
                                <td class="py-2 px-4">
                                    <Badge status={station.status}></Badge>
                                </td>
                                <td class="py-2 px-4">
                                    <a href="/contracts/{station.contract_name}/{station.number}">
                                        {station.name}
                                    </a>
                                </td>

                                <td class="font-semibold py-2 px-4">{station.available_bikes}/{station.bike_stands}</td>
                                <td >
                                    <div class="text-center bg-gray-200 rounded-full h-4 overflow-hidden relative">
                                        {#if station.available_bikes/station.bike_stands*100 >= 70}
                                            <div class="transition-all duration-1000 h-4 rounded-lg bg-green-400" style="width: {station.available_bikes/station.bike_stands*100}%"></div>
                                        {:else if station.available_bikes/station.bike_stands*100 >= 40}
                                        <div class="transition-all duration-1000 h-4 rounded-lg bg-orange-400" style="width: {station.available_bikes/station.bike_stands*100}%"></div>
                                        {:else}
                                        <div class="transition-all duration-1000 h-4 rounded-lg bg-red-500" style="width: {station.available_bikes/station.bike_stands*100}%"></div>
                                        {/if}
                                        <div class="absolute inline-block align-middle top-0 left-0 w-full text-center text-xs font-semibold  text-gray-800 rounded-lg">
                                            {Math.round(station.available_bikes/station.bike_stands*100)}%
                                        </div>
                                    </div>
                                </td>
                                <td class="py-2 px-4">{station.address.toLowerCase()}</td>
                            </tr>
                            {/each}
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>
{/if}