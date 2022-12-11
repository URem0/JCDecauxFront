<script>
    export let status;
</script>


{#if status == "OPEN"}
    <span class="text-xs inline-block py-1 px-2.5 leading-none text-center whitespace-nowrap align-baseline font-bold bg-green-500 text-white rounded-full">
        {status}
    </span>
{:else}
    <span class="text-xs inline-block py-1 px-2.5 leading-none text-center whitespace-nowrap align-baseline font-bold bg-red-500 text-white rounded-full">
        {status}
    </span>
{/if}
