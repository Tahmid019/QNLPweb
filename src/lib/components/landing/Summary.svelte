<script lang="ts">
  import { summaryData } from '$lib/data/summary.js'; 
</script>

<section id="summary" class="relative mx-auto mt-28 max-w-7xl px-6 text-center md:px-8">
<div class="max-w-4xl mx-auto px-4 py-6">
    <span
    class="pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-black to-gray-300/80 bg-clip-text text-center text-3xl md:text-4xl lg:text-5xl xl:text-6xl font-semibold font-poppins leading-none text-transparent dark:from-[var(--black-0)] dark:to-[var(--black-9)] mb-3 pb-3 md:pb-4 lg:pb-5"
  >
    {summaryData.title}
  </span>
    <p class="text-justify text-[0.5rem] md:text-[0.8rem] lg:text-[1rem] xl:text-[1.2rem] pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-[var(--black-0)] to-[var(--black-4)] bg-clip-text font-medium font-poppins leading-none text-transparent pt-3">
    {summaryData.content}
  </p>
</div>
</section>
