<script>
	import Footer from '$lib/layout/Footer.svelte';
	import Header from '$lib/layout/Header.svelte';
	
</script>

<svelte:head>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
  <link
    href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap"
    rel="stylesheet"
  />
</svelte:head>

<div class="min-h-screen bg-background font-sans antialiased">
	<Header />
	<div class="mx-auto flex-1 overflow-hidden">
		<slot></slot>
	</div>
	<Footer />
</div>
