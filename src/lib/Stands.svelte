<script>
    export let type = "occupied";
</script>


{#if type=="free"}
    <span class="text-xs inline-block py-1 px-2.5 leading-none text-center whitespace-nowrap align-baseline font-bold bg-green-500 text-white rounded-full">
        <slot></slot>
    </span>
{:else if type=="bank"}
    <span class="text-xs inline-block py-1 px-2.5 leading-none text-center whitespace-nowrap align-baseline font-bold bg-gray-500 text-white rounded-full">
        <slot></slot>
    </span>
{:else}
    <span class="text-xs inline-block py-1 px-2.5 leading-none text-center whitespace-nowrap align-baseline font-bold bg-red-500 text-white rounded-full">
        <slot></slot>
    </span>
{/if}