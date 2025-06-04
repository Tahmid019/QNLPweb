<script lang="ts">
  import { callForPapers } from '$lib/data/callForPapers'; 
  import Particles from '$lib/components/magic/Stars/Stars.svelte';

</script>

<section id="callForPapers" class="relative mx-auto mt-28 max-w-7xl px-6 text-center md:px-8">
<div
  class="relative flex p-4 text-center md:p-6 lg:p-8 flex-col items-center justify-center overflow-hidden rounded-lg border bg-background md:shadow-xl"
>
  <span
    class="pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-black to-gray-300/80 bg-clip-text text-center text-3xl md:text-4xl lg:text-5xl xl:text-6xl font-semibold font-poppins leading-none text-transparent dark:from-[var(--black-0)] dark:to-[var(--black-9)] pb-3 xl:pb-5"
  >
    {callForPapers.title}
  </span>
  <p class="text-justify text-[0.5rem] md:text-[0.8rem] lg:text-[1rem] xl:text-[1.2rem] pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-[var(--black-0)] to-[var(--black-4)] bg-clip-text font-medium font-poppins leading-none text-transparent">
    {callForPapers.description}
  </p>

  <ul class="self-start pl-10 text-left pt-3 text-[0.5rem] md:text-[0.8rem] lg:text-[1rem] xl:text-[1.2rem] font-poppins">
    {#each callForPapers.topics as topic}
      <li class="bg-gradient-to-b from-[var(--black-0)] to-[var(--black-4)] bg-clip-text text-transparent">• {topic}</li>
    {/each}
  </ul>
  
  <!-- <span
    class="pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-black to-gray-300/80 bg-clip-text text-center text-1xl md:text-2xl lg:text-3xl xl:text-4xl font-semibold font-poppins leading-none text-transparent dark:from-[var(--black-0)] dark:to-[var(--black-9)] pb-3 xl:pb-5"
  >
    {callForPapers.title}
  </span>
  <p class="text-justify text-[0.5rem] md:text-[0.8rem] lg:text-[1rem] xl:text-[1.2rem] pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-[var(--black-0)] to-[var(--black-4)] bg-clip-text font-medium font-poppins leading-none text-transparent">
    {callForPapers.description}
  </p>
  <span
    class="pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-black to-gray-300/80 bg-clip-text text-center text-1xl md:text-2xl lg:text-3xl xl:text-4xl font-semibold font-poppins leading-none text-transparent dark:from-[var(--black-0)] dark:to-[var(--black-9)] pb-3 xl:pb-5"
  >
    {callForPapers.title}
  </span>
  <p class="text-justify text-[0.5rem] md:text-[0.8rem] lg:text-[1rem] xl:text-[1.2rem] pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-[var(--black-0)] to-[var(--black-4)] bg-clip-text font-medium font-poppins leading-none text-transparent">
    {callForPapers.description}
  </p> -->
  <p class="text-[0.5rem] md:text-[0.8rem] lg:text-[1rem] xl:text-[1.2rem] font-poppins bg-gradient-to-b from-[var(--black-4)] to-[var(--black-9)] bg-clip-text text-transparent italic mt-3">{callForPapers.note}</p>
  <Particles className="absolute inset-0" quantity={350} color={"000000"} size=0.6 />
</div>
</section>