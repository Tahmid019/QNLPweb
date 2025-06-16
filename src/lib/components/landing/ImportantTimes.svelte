<script lang="ts">
  import { callForPapers } from '$lib/data/callForPapers'; 
  import Particles from '$lib/components/magic/Stars/Stars.svelte';

</script>
<section id="importantTimes" class="relative mx-auto mt-28 max-w-7xl px-6 text-center md:px-8">
  <div
  class="relative flex p-4 text-center md:p-6 lg:p-8 flex-col items-center justify-center overflow-hidden rounded-lg border bg-background md:shadow-xl"
>
    <span
    class="pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-black to-gray-300/80 bg-clip-text text-center text-3xl md:text-4xl lg:text-5xl xl:text-6xl font-semibold font-poppins leading-none text-transparent dark:from-[var(--black-0)] dark:to-[var(--black-9)] pb-3 xl:pb-5"
  >
    Important Dates
  </span>

  <ul class="mt-8 w-full flex flex-col items-center space-y-6 ">
    {#each callForPapers.timeline as { event, date }, idx}
      <li class="flex items-start space-x-4 w-full max-w-xl bg-red-50 rounded-lg p-3 shadow-lg ">
        <!-- Dot indicator -->
        <div class="relative mt-1 flex flex-col items-center">
          <span
            class="block h-3 w-3 rounded-full bg-red-500 "
          />
        
        </div>

        <!-- Event content -->
        <div class="flex-1 text-left ">
            <p class="font-semibold text-lg text-gray-800 flex items-center gap-3">
            {event}
            <time
              class="inline-block rounded-full bg-gradient-to-tr from-red-500 to-red-300 px-3 py-1 text-sm font-medium text-white ml-3"
              datetime={date}
            >
              {date}
            </time>
            </p>
        </div>
      </li>
    {/each}
  </ul>
  <Particles className="absolute inset-0" quantity={350} color={"000000"} size=0.6 />
</div>
</section>
