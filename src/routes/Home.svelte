<script>
  import { onMount } from "svelte";
  import { activeStore } from "../stores";
  import Welcometext from "../components/Welcome.svelte";

  let init = false;

  onMount(() => {
    init = true;
  });

  // let visible = true;

  // function typewriter(node, { speed = 50 }) {
  // 	const valid = (
  // 		node.childNodes.length === 1 &&
  // 		node.childNodes[0].nodeType === Node.TEXT_NODE
  // 	);

  // 	if (!valid) {
  // 		throw new Error(`This transition only works on elements with a single text node child`);
  // 	}

  // 	const text = node.textContent;
  // 	const duration = text.length * speed;

  // 	return {
  // 		duration,
  // 		tick: t => {
  // 			const i = ~~(text.length * t);
  // 			node.textContent = text.slice(0, i);
  // 		}
  // 	};
  // }
</script>

<!-- <h1>{$activeStore}</h1> -->
{#if init}
  <Welcometext />
{/if}

<!-- <label>
    <input type="checkbox" bind:checked={visible}>
    visible
  </label> -->
<!--
  {#if visible}
    <h1 in:typewriter>
      The quick brown fox jumps over the lazy dog
    </h1>
  {/if} -->
