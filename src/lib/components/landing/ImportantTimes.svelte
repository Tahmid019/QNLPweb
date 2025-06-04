<script lang="ts">
  import { callForPapers } from '$lib/data/callForPapers'; 
  import Particles from '$lib/components/magic/Stars/Stars.svelte';

</script>
<section id="importantTimes" class="relative mx-auto mt-28 max-w-7xl px-6 text-center md:px-8">
    <span
    class="pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-black to-gray-300/80 bg-clip-text text-center text-3xl md:text-4xl lg:text-5xl xl:text-6xl font-semibold font-poppins leading-none text-transparent dark:from-[var(--black-0)] dark:to-[var(--black-9)] pb-3 xl:pb-5"
  >
    Important Dates
  </span>

  <ul class="pl-2 md:pl-32 lg:pl-52 xl:pl-72 text-left pt-3 text-[0.55rem] md:text-[0.85rem] lg:text-[1.05rem] xl:text-[1.25rem] font-poppins">
    {#each callForPapers.timeline as topic}
      <li class=" bg-gradient-to-b from-[var(--black-0)] to-[var(--black-4)] bg-clip-text text-transparent">• {topic.event} --- {topic.date}</li>
      {/each}
  </ul>

    <!-- <div class="group timeline flex flex-col justify-start self-start w-full">
    {#each callForPapers.timeline as ev }
    <div class="timeline-cont flex flex-row m-1 md:m-2 lg:m-3 bg-slate-600/10 border rounded-lg ">
      <div class="eve-cont w-[65%] flex justify-start p-1">
        <span
        class="self-center pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-black to-gray-300/80 bg-clip-text text-start md:text-xl lg:text-3xl xl:text-4xl font-semibold font-poppins leading-none text-transparent dark:from-[var(--black-0)] dark:to-[var(--black-9)] "
        >
        {ev.event}
      </span>
    </div>
    <div class="eve-dat flex justify-start self-center w-[35%] p-1">
      <p class="text-left text-[0.5rem] md:text-[0.8rem] lg:text-[1rem] xl:text-[1.2rem] pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-[var(--black-0)] to-[var(--black-4)] bg-clip-text font-medium font-poppins leading-none text-transparent">
        {ev.date}
      </p>
    </div>
  </div>
  {/each}
</div> -->
</section>
