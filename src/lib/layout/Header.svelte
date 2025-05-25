<script lang="ts">
  import { cn } from '$lib/utils';
  import { AlignJustify, XIcon } from 'lucide-svelte';
  import { fly, fade } from 'svelte/transition';

  const menuItem = [
    { id: 1, label: 'About', href: '#' },
    { id: 2, label: 'Timeline', href: '#' },
    { id: 3, label: 'Organizers', href: '#' },
  ];

  let hamburgerMenuIsOpen = false;

  function toggleOverflowHidden(node: HTMLElement) {
    node.addEventListener('click', () => {
      hamburgerMenuIsOpen = !hamburgerMenuIsOpen;
      const html = document.querySelector('html');
      if (html) {
        html.classList.toggle('overflow-hidden', hamburgerMenuIsOpen);
      }
    });
  }

  let innerWidth = 0;
</script>

<svelte:window bind:innerWidth />

<header class="fixed left-0 top-0 z-50 w-full -translate-y-4 animate-fade-in border-b opacity-0 backdrop-blur-md">
  <div class="container flex h-14 items-center justify-between">
    <a class="text-md font-extrabold flex items-center" href="/">QNLP</a>

    <!-- Desktop nav -->
    {#if innerWidth >= 768}
      <nav>
        <ul class="flex space-x-6 uppercase">
          {#each menuItem as item}
            <li>
              <a class="text-sm hover:text-gray-700 transition-colors" href={item.href}>
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
          <a class="text-xl hover:text-gray-700 transition-colors" href={item.href}>
            {item.label}
          </a>
        </li>
      {/each}
    </ul>
  {/if}
</nav>