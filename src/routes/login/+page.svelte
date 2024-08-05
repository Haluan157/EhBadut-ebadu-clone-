<script>
import { goto } from '$app/navigation';
  import { link, theme } from '$lib/get';
  import { onMount } from 'svelte'
  let a =''
  let hych = false
  // Lakukan navigasi berdasarkan kondisi `link`
  onMount(()=> {
    $link = localStorage.getItem("user") || ""
    if ($link) {
    goto('/dashboard');
  } else {
    goto('/login');
  }})
  function aha() {
    a = a.trim()
    if (a) {
      localStorage.setItem("user",a)
      goto('/dashboard')
    }
    else {
      hych = true
    }
  }
  function handle(e) {
    if (e.key === "Enter") {
      e.preventDefault();
      aha()
    }
  }
</script>
<div class="flex h-full p-7 justify-center items-center">
  <div class="{$theme ? "bg-blue-100":"bg-neutral"} bg-opacity-20 w-full rounded-lg shadow bg-blur-3xl flex flex-col items-center py-3 px-16 gap-4">
    <h1 class="font-roboto font-bold text-2xl">LOGIN</h1>
    <input type="text" class="border-b border-black bg-transparent focus:outline-none {!$theme ? "placeholder:text-slate-700":"placeholder:text-zinc-600"} focus:border-teal-400" placeholder="Masukkan Nama" bind:value={a} on:keydown={handle}>
    <div class="w-full bg-teal-200 text-sm py-2 text-center text-teal-600 font-roboto rounded-lg border-2 border-teal-600" class:hidden={!hych}>ISI NAMAMU</div>
    <button class="btn w-full rounded-full text-roboto" on:click={aha}>Masuk</button>
    <span class="text-roboto text-sm text-center">No copyright. All Rights Reserved<br>Powered by <a href="https://github.com/Haluan157" class="haha">Haluan157</a></span>
  </div>
</div>
