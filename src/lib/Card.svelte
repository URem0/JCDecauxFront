<script>
    import NamespaceCardTitle from '$lib/CardTitle.svelte';
    export let title = '';
    let class_='';
    export {class_ as class};
</script>



<div class="{class_} space-y-2">
    {#if title}
        <span class="inline-flex text-sm font-medium text-gray-500 dark:text-gray-200">
            <NamespaceCardTitle {title} />
        </span>
    {/if}
    <div
        class="bg-white dark:bg-slate-800 text-gray-500 dark:text-gray-200 px-4 py-6 shadow rounded-lg overflow-hidden"
    >
        <slot />
    </div>
</div>

