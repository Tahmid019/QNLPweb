<script lang="ts">
  import { callForPapers } from '$lib/data/callForPapers'; 
  import Particles from '$lib/components/magic/Stars/Stars.svelte';

</script>
<section id="importantTimes" class="relative mx-auto mt-28 max-w-7xl px-6 text-center md:px-8">
    <div
  class="relative flex p-4 text-center md:p-6 lg:p-8 flex-col items-center justify-center overflow-hidden rounded-lg border bg-background md:shadow-xl"
>
    <span
    class="pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-black to-gray-300/80 bg-clip-text text-center text-2xl md:text-3xl lg:text-4xl xl:text-5xl font-semibold font-poppins leading-none text-transparent dark:from-[var(--black-0)] dark:to-[var(--black-9)] pb-3 xl:pb-5"
  >
    Paper Submission
  </span>

  <div class="container-submission w-auto h-auto bg-red-100 p-3 rounded-lg shadow-lg ">

    <p class="text-center text-[0.5rem] md:text-[0.8rem] lg:text-[1rem] xl:text-[1.2rem] bg-gradient-to-b from-[var(--black-0)] to-[var(--black-4)] bg-clip-text font-medium font-poppins leading-none text-transparent">
      Open Review | Please Login First & then click on the Link
      <a
        href="https://openreview.net/group?id=aclweb.org/AACL-IJCNLP/2025/Workshop/QuantumNLP#tab-your-consoles"
        class="underline text-blue-600 hover:text-blue-800"
        style="pointer-events: auto;"
        >Click Here</a
      >
    </p>
  </div>
  <Particles className="absolute inset-0" quantity={350} color={"000000"} size=0.6 />
  </div>
</section>
