<script>
  import Particles from '$lib/components/magic/Stars/Stars.svelte';

  let motivation_text = "Natural Language Processing (NLP) is a promising area of Artificial Intelligence (AI) that enables machines to understand, process, and generate human language. However, the exponential growth of data demands enormous computing resources to process NLP tasks, making them inaccessible to everyone. On the other hand, quantum computing leverages the quantum mechanics principles that offer new computational paradigms to address these challenges. Moreover, quantum algorithms show potential speedups compared to their classical counterparts for specific computational tasks such as prime factorization, searching, and solving linear algebra. The capability of quantum computing to handle complex computation and large data sets holds promise to revolutionize NLP tasks more efficiently. To harness the power of the quantum computing paradigm, it is essential to bring together a diverse group of experts from NLP, quantum computing, machine learning, and quantum machine learning. Collaboration inse fields is key to addressing the complex challenges in this domain. To support and accelerate progress in this rapidly evolving area, we designed the IJCNLP workshop, aimed at fostering discussions on recent developments in quantum algorithms and quantum machine learning techniques to revolutionize NLP. This workshop aims to explore the intersection of quantum computing and NLP, introducing participants to the foundational concepts of quantum information and demonstrating how quantum algorithms and quantum machine learning (QML) models can be applied to key NLP tasks.";
</script>

<div
  class="relative flex p-4 text-center md:p-6 lg:p-8 flex-col items-center justify-center overflow-hidden rounded-lg border bg-background md:shadow-xl"
>
  <span
    class="pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-black to-gray-300/80 bg-clip-text text-center text-2xl md:text-3xl lg:text-4xl xl:text-5xl font-semibold font-poppins leading-none text-transparent dark:from-[var(--black-0)] dark:to-[var(--black-9)] pb-3 xl:pb-5"
  >
    Motivation
  </span>
  <p class="text-justify text-[0.5rem] md:text-[0.8rem] lg:text-[1rem] xl:text-[1.2rem] pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-[var(--black-0)] to-[var(--black-4)] bg-clip-text font-medium font-poppins leading-none text-transparent">
    {motivation_text}
  </p>
  <Particles className="absolute inset-0" quantity={350} color={"000000"} size=0.6  />
</div>
