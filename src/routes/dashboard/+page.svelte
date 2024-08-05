<script>
import { goto } from '$app/navigation';
  import { link } from '$lib/get';
  import { onMount } from 'svelte'

  // Lakukan navigasi berdasarkan kondisi `link`
  onMount(()=> {
  $link = localStorage.getItem("user") || ""
    if ($link) {
    goto('/dashboard');
  } else {
    goto('/login');
  }})
  function yah() {
    localStorage.removeItem("user")
    goto("/login")
  }
</script>
<div class="pt-16 h-full">
<h1>{$link}</h1>
<button class="btn" on:click={yah}>uju</button>
</div>