<script>
  import { activeStore, projectStore } from "../stores.js";
  export let keyword;
  export let src;
  export let cat;

  const setActive = () => {
    $activeStore = keyword;
    $projectStore = null;
  };
</script>

<button class:active={$activeStore == keyword} on:click={setActive}
class:bottom={src != null}
class:primary={cat === "primary"}
>
  {#if src}
    <img {src} alt={keyword} width="30" />
  {/if}
  <span>{`${keyword}`}</span>
</button>

<style>

button:not(.bottom) {
    font-weight: 500;
    font-size: 1.8rem;
    max-height: 53px;
    color: var(--bg-light);
    padding: 1rem min(15px, 10%);
    transition: background-color 200ms;
    margin-top: 1rem;
    border-bottom: 5px solid transparent;
    margin: 1rem;
  }
  button:not(.bottom):hover {
    cursor: pointer;
    font-weight: 900;
  }
  .bottom {
    font-size: 10px;
    color: var(--accent);
    display: grid;
    grid-template-rows: 2fr 1fr;
    /* margin-bottom: 5px;  */
    min-height: 100%;
  }
  .bottom > * {
    margin: auto;
  }
  .bottom:not(.active){
    filter: grayscale(100%) brightness(150%);
  }
  img[alt="My Strategy"]{
    margin-bottom: 4px;
  }
  img[alt="Home"]{
    margin-bottom: 2px;
  }
  button.primary{
    color: var(--text);
    font-size: 1.5em;
  }

  @media only screen and (max-width: 683px){
    button:not(.bottom):not(.primary){
      display: none;
    }
  }
</style>
