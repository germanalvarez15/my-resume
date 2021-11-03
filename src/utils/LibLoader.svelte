<svelte:head>
  <script bind:this={spt} src={url} />
</svelte:head>

<script>
  import { onMount, createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();
  export let url;
  let spt;

  onMount(async () => {
    spt.addEventListener('load', () => {
      dispatch('loaded');
    })

    spt.addEventListener('error', (event) => {
      console.error("something went wrong", event);
      dispatch('error');
    });
  });
</script>