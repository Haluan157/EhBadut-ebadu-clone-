<script>
  import "../app.css"
  import { onMount } from 'svelte'
  import { theme } from "$lib/get"
  const change = () => {
    $theme = !$theme;
    localStorage.setItem("themes", $theme.toString())
  }
  import Fyy from '$lib/img.svelte'
  onMount(() => {
    const hay = localStorage.getItem("themes") || true;
    $theme = hay === "true"
  })
</script>
  
<header data-theme={$theme ? "light":"dark"} class="fixed t-0 z-50 w-full flex w-full h-16 p-3 items-center justify-between {$theme ? 'shadow':'border-b border-slate-800'} transition-colors duration-300">
  <div class="flex flex-row">
  <img src="/d429b45e-d3ed-437e-89b5-a9196536f330.png" class="w-7 h-7" alt='ebadu-image'>
  <span class="font-oswald font-bold text-xl ml-1">EBADU</span>
  </div>
  <div>
  <button class="btn btn-transparent" on:click={change}>
    {#if $theme}
    <Fyy name='sun' />
    {:else}
    <Fyy name='moon' />
    {/if}
  </button>
  </div>
</header>

<main data-theme={$theme ? "light":"dark"} class="h-full transition-colors duration-300">
  <slot />
</main>