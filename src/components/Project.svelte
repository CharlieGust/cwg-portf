<script>
  import { activeStore, projectStore, langStore } from "../stores";
  export let title;
  export let desc;
  // export let subtitle;
</script>

<style>

</style>

<div id="divProjekt">
  <button class="transperant" on:click={() => ($projectStore = null)}> back </button>
  <h1>{title}</h1>
  <p>{desc}</p>
  <!-- <h1>{subtitle}</h1> -->
</div>

