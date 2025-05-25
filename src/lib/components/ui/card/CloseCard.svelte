<script lang="ts">
    import { slide } from 'svelte/transition';

    export let title: string = 'Title';
    export let subtitle: string = '';
    export let text: string = 'Text ... ';

    let isOpen = false;

    const toggle = () => {
        isOpen = !isOpen;
    };
</script>

<div class="w-full mx-auto  rounded-lg shadow-sm hover:shadow-md transition-shadow duration-200 ease-in-out border ">
    <button
        type="button"
        on:click={toggle}
        class="w-full text-left px-4 py-3 cursor-pointer transition-colors duration-200 focus:outline-none"
        aria-expanded={isOpen}
        aria-controls="card-content"
    >
        <h3 class="text-sm md:text-lg xl:text-xl text-center font-semibold font-poppins text-white">{title}</h3>
        {#if subtitle}
            <p class="text-sm text-center font-poppins text-gray-400 mt-1">{subtitle}</p>
        {/if}
        {#if isOpen}
            <div
                id="card-content"
                transition:slide
                class="lg:px-4 py-2 lg:py-3 border-t border-gray-700"
            >
                <p class="text-gray-400 text-justify text-[0.5rem] md:text-[0.6rem] lg:text-[0.8rem] xl:text-[1rem] leading-relaxed">{text}</p>
            </div>
        {/if}
    </button>
</div>