<script>
     export let contracts_list
	 export let headers
</script>


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
						{#each contracts_list as contract}
						<tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700">
							<td class="font-semibold py-2 px-4">
								<a href="/contracts/{contract.name}">
									{contract.name.toUpperCase()}
								</a>
							</td>
							<td class="py-2 px-4">{contract.commercial_name}</td>
							<td class="py-2 px-4">{contract.country_code}</td>
						</tr>
						{/each}
					</tbody>
				</table>
			</div>
		</div>
	</div>
</div>