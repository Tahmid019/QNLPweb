<script lang="ts">
    import ProfBar from '$lib/components/ui/profile/profBar.svelte';
    import speakers from '$lib/data/speakers';
    import Particles from '$lib/components/magic/Stars/Stars.svelte';
</script>

<section id="speakers" class="relative mx-auto mt-28 max-w-7xl px-6 text-center md:px-8">
	<div
  class="relative flex p-4 text-center md:p-6 lg:p-8 flex-col items-center justify-center overflow-hidden rounded-lg border bg-background md:shadow-xl"
>
    <h1 class=" mb-6 r pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-gray-600 to-gray-300/80 bg-clip-text text-center text-2xl md:text-3xl lg:text-4xl xl:text-5xl font-semibold font-poppins leading-none text-transparent dark:from-[var(--black-0)] dark:to-[var(--black-9)]">Speakers</h1>
        
        <div class="flex justify-center items-center">
            <div class="grid place-items-center grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
                {#each speakers as profile}
                    <ProfBar name={profile.title} designation={profile.description} link={profile.link} profImg={profile.progImage} />
                {/each}
            </div>
        </div>

     <Particles className="absolute inset-0" quantity={350} color={"000000"} size=0.6 />
  </div>
</section>