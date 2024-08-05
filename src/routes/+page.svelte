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
</script>