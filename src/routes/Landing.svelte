<script>
  import { activeStore } from "../stores";
  import { onMount } from "svelte";
  import Welcometext from "../components/Welcome.svelte";
  import Box from "../components/Box.svelte";


  let init = false;

  onMount(() => {
    init = true;
  });
</script>
<div>
<Box>
  {#if init}
  <Welcometext />
{/if}
  <button on:click={() => ($activeStore = "Home")}> click me </button>
</Box>
</div>
<style>
  div {
    height: 200px;
    position: relative;

  }
  button {
    width: 100%;
    height: 100%;
  }
</style>
