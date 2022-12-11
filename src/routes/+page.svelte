<script>
	const features = [
        {
            name: 'Stations',
            description:
                'Access to the list of all JCDecaux stations',
            href: '/stations'
        },
        {
            name: 'Contracts',
            description:
                'Access to the list of all JCDecaux contracts',
            href: '/contracts'
        }
    ];
</script>



<div class="py-16 sm:py-24">
    <div class="mx-auto max-w-md px-4 text-center sm:max-w-3xl sm:px-6 lg:max-w-7xl lg:px-8">
        <p
            class="mt-2 text-3xl font-extrabold tracking-tight text-gray-800 dark:text-white sm:text-5xl"
        >
            WELCOME to JCDecaux dashboard
        </p>
        <p class="mx-auto mt-5 max-w-prose text-xl text-gray-500">
           RTS Project
        </p>
        <div class="mt-12">
            <div class="grid grid-cols-1 gap-8 sm:grid-cols-1 lg:grid-cols-2">
                {#each features as feature}
                    <div class="pt-6">
                        <a href={feature.href}>
                            <div
                                class="flow-root rounded-lg bg-gray-50 hover:bg-gray-100 px-6 pb-8 dark:bg-gray-800  dark:hover:bg-gray-700 shadow"
                            >
                                <div class="-mt-6">
                                    <div>
                                        <span
                                            class="inline-flex items-center justify-center rounded-md bg-blue-500 p-3 shadow-lg"
                                        >
                                        </span>
                                    </div>
                                    <h3
                                        class="mt-8 text-lg font-medium text-gray-900 dark:text-white"
                                    >
                                        {feature.name}
                                    </h3>
                                    <p class="mt-5 text-base text-gray-500 dark:text-gray-400">
                                        {feature.description}
                                    </p>
                                </div>
                            </div>
                        </a>
                    </div>
                {/each}
            </div>
        </div>
    </div>
</div>
