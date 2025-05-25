<script lang="ts">
    import { onMount } from 'svelte';

  import { cn } from '$lib/utils';
  import { AlignJustify, XIcon } from 'lucide-svelte';
  import { fly, fade } from 'svelte/transition';

  const menuItem = [
    {id: 1, label: '', href: '/'},
    { id: 2, label: 'Motivation', href: '/' },
    { id: 3, label: 'Call For Papers', href: '/' },
    { id: 4, label: 'Organizers', href: '/' },
  ];

  let hamburgerMenuIsOpen = false;

  function toggleOverflowHidden(node: HTMLElement) {
    node.addEventListener('click', () => {
      hamburgerMenuIsOpen = !hamburgerMenuIsOpen;
      updateOverflowHidden();
    });
  }

  function updateOverflowHidden() {
    const html = document.querySelector('html');
    if (html) {
      html.classList.toggle('overflow-hidden', hamburgerMenuIsOpen);
    }
  }

  // Close menu and remove overflow-hidden when hash changes
  function handleHashChange() {
    hamburgerMenuIsOpen = false;
    updateOverflowHidden();
  }

  // Add hash change listener
 onMount(() => {
    // Enable smooth scrolling for anchor links
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', (e: Event) => {
        e.preventDefault();
        const target = e.currentTarget as HTMLAnchorElement;
        const href = target.getAttribute('href');
        if (href) {
          const el = document.querySelector(href);
          if (el) {
            el.scrollIntoView({
              behavior: 'smooth'
            });
          }
        }
      });
    });
  });
  let innerWidth = 0;
</script>

<svelte:window bind:innerWidth />

<header class="fixed left-0 top-0 z-50 w-full -translate-y-4 animate-fade-in border-b opacity-0 backdrop-blur-md">
  <div class="container flex h-14 items-center justify-between">
    <!-- <a class="text-md font-extrabold flex items-center" href="/">QNLP</a> -->
     <a href="/" class="flex items-center gap-2">
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="50" height="35" viewBox="0 0 252 121">
          <image xlink:href="data:image/png;base64,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" x="0" y="0" width="252" height="121"/>
        </svg>
      </a>

    <!-- Desktop nav -->
    {#if innerWidth >= 768}
      <nav>
        <ul class="flex space-x-6 uppercase">
          {#each menuItem as item}
            <li>
              <a 
                href={item.href}
                on:click|preventDefault={(e) => {
                  hamburgerMenuIsOpen = false;
                  const el = document.querySelector(item.href);
                  if (el) {
                    el.scrollIntoView({ behavior: 'smooth' });
                  }
                }}
              >
                {item.label}
              </a>
            </li>
          {/each}
        </ul>
      </nav>
    {/if}

    <!-- Mobile toggle -->
    <button class="md:hidden z-50 relative" use:toggleOverflowHidden>
      <span class="sr-only">Toggle menu</span>
      {#if hamburgerMenuIsOpen}
        <XIcon on:click={() => hamburgerMenuIsOpen = false} strokeWidth={1.4} class="text-gray-300" />
      {:else}
        <AlignJustify on:click={() => hamburgerMenuIsOpen = true} strokeWidth={1.4} class="text-gray-300" />
      {/if}
    </button>
  </div>
</header>

<!-- Mobile nav overlay -->
<nav
  class={cn(
    `fixed left-0 top-0 z-40 h-screen w-full overflow-auto bg-background/70 backdrop-blur-md`,
    {
      'pointer-events-none opacity-0': !hamburgerMenuIsOpen,
      'pointer-events-auto opacity-100': hamburgerMenuIsOpen
    }
  )}
  transition:fade
>
  {#if hamburgerMenuIsOpen}
    <ul in:fly={{ y: -30, duration: 400 }} class="flex flex-col uppercase space-y-4 pt-16 pl-6">
      {#each menuItem as item}
        <li>
          <a 
            class="text-xl hover:text-gray-700 transition-colors" 
            href={item.href}
            on:click={() => {
              hamburgerMenuIsOpen = false;
              updateOverflowHidden();
            }}
          >
            {item.label}
          </a>
        </li>
      {/each}
    </ul>
  {/if}
</nav>