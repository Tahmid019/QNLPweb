<script lang="ts">
	import cube_gif from '$lib/imgs/gif/black_cube.gif';
</script>

<section id="hero" class="relative z-30 mx-auto mt-14 md:mt-24 lg:mt-32 max-w-7xl px-6 text-center md:px-8">
	<div class="hero-container relative flex flex-col-reverse lg:flex-row xl:-translate-x-16">
		<div class="left-container relative lg:w-[70%]">
			<h1
				class="-translate-y-4 animate-fade-in text-balance font-poppins lg:text-right bg-gradient-to-br from-[var(--black-0)] from-30% to-[var(--black-4)] bg-clip-text pt-6 text-5xl font-semibold leading-none tracking-tighter text-transparent opacity-0 [--animation-delay:200ms] dark:from-[var(--black-0)] dark:to-[var(--black-9)] sm:text-6xl md:text-7xl lg:text-8xl"
			>
				QuantumNLP
			</h1>
			<h2
				class="-translate-y-4 animate-fade-in text-balance font-poppins lg:text-right bg-gradient-to-br from-[var(--white-0)] from-30% to-[var(--white-0)]/40 bg-clip-text pb-6 pt-2 text-2xl font-medium leading-none tracking-tighter text-transparent opacity-0 [--animation-delay:200ms] dark:from-red-500 dark:to-red-300 sm:text-3xl md:text-4xl lg:text-5xl"
			>
				Integrating Quantum Computing with Natural Language Processing
			</h2>
			<p
				class="mb-12 -translate-y-4 animate-fade-in text-balance font-poppins lg:text-right text-lg tracking-tight text-gray-600 opacity-0 [--animation-delay:400ms] md:text-xl"
			>
				
				Under 14th <a href="https://www.afnlp.org/conferences/ijcnlp2025/" class="underline underline-offset-2">IJCNLP-AACL</a> 2025 Workshop Mumbai, India.<br> Tentative date: Dec 23-24, 2025
			</p>
		</div>
		<div class="right-container relative lg:w-[30%] self-center max-w-96">
			<img src={cube_gif} alt="cube_gif">
		</div>
	</div>
</section>