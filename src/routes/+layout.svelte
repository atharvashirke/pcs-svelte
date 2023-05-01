<script lang="ts">
  import "../app.postcss";
  import Navbar from "$lib/components/Navbar.svelte";
  import { invalidate } from "$app/navigation";
  import { onMount } from "svelte";
  import type { LayoutData } from "./$types";

  export let data: LayoutData;
  let toggleReverse=true;

  $: ({ supabase, session } = data);

  onMount(() => {
    const { data } = supabase.auth.onAuthStateChange((event, _session) => {
      if (_session?.expires_at !== session?.expires_at) {
        invalidate("supabase:auth");
      }
    });

    return () => data.subscription.unsubscribe();
  });
</script>
<div class="overscroll-y-contain overflow-auto">
  <Navbar/>

  <div class="h-full w-full m-0 p-0 prose lg:prose-xl flex flex-col">
    <slot/>
  </div>

  {#if toggleReverse}
    <video id="video-background" autoplay loop on:ended={toggleReverse=false}>
        <source src="/fluidGradient.mp4" type="video/mp4"/>
    </video>
  {:else}
    <video id="video-background" autoplay loop on:ended={toggleReverse=true}>
        <source src="/fluidGradientReverse.mp4" type="video/mp4"/>
    </video>
  {/if}
</div>



<style>
  #video-background {
          position: fixed;
          right: 0;
          bottom: 0;
          min-width: 100%;
          min-height: 100%;
          z-index: -100;
      }
</style>