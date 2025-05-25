<script lang="ts">
    import ProfBar from '$lib/components/ui/profile/profBar.svelte';
    import developers from '$lib/data/developers';
</script>

<section id="developers" class="relative mx-auto mt-28 max-w-7xl px-6 text-center md:px-8">
	<div class="container mx-auto px-4">
    <h1 class=" mb-6 r pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-gray-600 to-gray-300/80 bg-clip-text text-center text-3xl md:text-4xl lg:text-5xl xl:text-6xl font-semibold font-poppins leading-none text-transparent dark:from-white dark:to-slate-700/10">developers</h1>
        
        <div class="flex justify-center items-center">
            <div class="grid place-items-center grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
                {#each developers as profile}
                    <ProfBar name={profile.title} designation={profile.description} link={profile.link} />
                {/each}
            </div>
        </div>

    </div>
</section>