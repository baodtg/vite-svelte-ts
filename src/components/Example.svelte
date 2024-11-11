

<script lang="ts">
  import { getContext } from "svelte"
  import svelteLogo from '/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from '../lib/Counter.svelte'
  import { writable } from 'svelte/store';
  import { createQuery } from '@tanstack/svelte-query'
  import type { AppContext } from "../App.svelte"

  const { dispatch } = getContext<AppContext>('app');

  console.log({ dispatch })

   const query = createQuery({
    queryKey: ['todos'],
    queryFn: () => [],
  })

  const count = writable(0);
	console.log($count); // logs 0

	count.set(1);
	console.log($count); // logs 1

	$count = 2;
	console.log($count); // logs 2
</script>

<div>
<a href="https://vite.dev" target="_blank" rel="noreferrer">
  <img src={viteLogo} class="logo" alt="Vite Logo" />
</a>
<a href="https://svelte.dev" target="_blank" rel="noreferrer">
  <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
</a>
</div>
<h1>Vite + Svelte</h1>

<div class="card">
<Counter />
</div>

<p>
Check out <a href="https://github.com/sveltejs/kit#readme" target="_blank" rel="noreferrer">SvelteKit</a>, the official Svelte app framework powered by Vite!
</p>

<p class="read-the-docs">
Click on the Vite and Svelte logos to learn more
</p>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>
