<svelte:options customElement="my-app" />

<script lang="ts">
  import {onMount,setContext} from "svelte"
  import styleUrl from "./main.css?url";
  import Example from "./components/Example.svelte"
  import { QueryClient, QueryClientProvider } from '@tanstack/svelte-query'

  const queryClient = new QueryClient()

  function dispatch<T>(type: string, detail: T) {
    $host().dispatchEvent(
      new CustomEvent(type, {
        detail,
      })
    );
  }

  const { greet } = $props();

  export const someMethod = () => {
    console.log("Hello")
  }

  onMount(()=>{
      dispatch('ready', { greet })
  })

  const context = {
    dispatch
  }
  
  export type AppContext = typeof context;

  setContext('app', context);

</script>

<main id="app">
  <QueryClientProvider client={queryClient}>
    <Example />
  </QueryClientProvider>
</main>

<link rel="stylesheet" href={styleUrl}/>