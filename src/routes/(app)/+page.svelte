<script lang="ts">
	import { seo } from '$lib';
	import CallForPapers from '$lib/components/landing/CallForPapers.svelte';
	import Comittee from '$lib/components/landing/Comittee.svelte';
	import Developers from '$lib/components/landing/Developers.svelte';
	import HeroSection from '$lib/components/landing/HeroSection.svelte';
	import MotivationSection from '$lib/components/landing/MotivationSection.svelte';
	import Organizers from '$lib/components/landing/Organizers.svelte';
	import Speakers from '$lib/components/landing/Speakers.svelte';
	import Summary from '$lib/components/landing/Summary.svelte';
	import WorkshopGoals from '$lib/components/landing/WorkshopGoals.svelte';
	import SphereMask from '$lib/components/magic/SphereMask/SphereMask.svelte';

</script>

<svelte:head>
	<title>{seo.title}</title>
	<meta name="description" content={seo.description} />
	<meta name="keywords" content={seo.keywords} />

	<meta property="og:title" content={seo.title} />
	<meta property="og:description" content={seo.description} />
	<meta property="og:image" content={seo.image} />
	<meta property="og:site_name" content={seo.title} />
	<meta property="og:url" content={seo.url} />

	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content={seo.title} />
	<meta name="twitter:description" content={seo.description} />
	<meta name="twitter:image" content={seo.image} />
	<meta name="twitter:site" content="@tahmid019" />

	<link rel="preconnect" href="https://fonts.googleapis.com">
</svelte:head>

<HeroSection />
<MotivationSection />
<WorkshopGoals />
<CallForPapers />
<Organizers />
<Comittee />
<Speakers />
<Developers />
<Summary />
<SphereMask />
