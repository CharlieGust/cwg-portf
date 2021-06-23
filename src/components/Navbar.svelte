<script>
  import { fly, fade } from "svelte/transition";
  import { circInOut } from "svelte/easing";

  import NavLink from "./NavLink.svelte";
  import { activeStore } from "../stores.js";

  const src = null;
  const cat = null;
  const p = "primary";
  const s = "secondary";

  let overlay = false;
  const toggleOverlay = () => {
    if (overlay === false) {
      overlay = true;
    } else {
      overlay = false;
    }
  };

  document.addEventListener("click", (e) => {
    if (!e.target.closest("#sidenav") && !e.target.closest(".menu")) {
      overlay = false;
    }
  });
</script>

<nav class="navbar">
  <div class="container">
    <button on:click={() => ($activeStore = "Home")}>
      <img src="../cglogga1.png" alt="svelte" height="50" />
    </button>
    <div class="links">
      <NavLink keyword="Projekt" {src} cat={false} />
      <NavLink keyword="Skills" {src} cat={false} />
      <NavLink keyword="Kontakt" {src} cat={false} />
      <button class="menu" on:click={toggleOverlay}>
        <img src="../hamburger.png" alt="Menu" width="35" height="40" />
      </button>
    </div>
  </div>
</nav>

{#if overlay}
  <aside
    transition:fly={{ x: 500, duration: 300, easing: circInOut }}
    id="sidenav"
  >
    <button class="close" on:click={toggleOverlay}>
      <img src="./svg/close.svg" alt="Close" />
    </button>
    <NavLink keyword="Hem" {src} cat={p} />
    <NavLink keyword="Projekt" {src} cat={p} />
    <NavLink keyword="Skills" {src} cat={p} />
    <NavLink keyword="Kontakt" {src} cat={p} />
  </aside>
{/if}

<style>
  nav.navbar {
    background: var(--bg-dark);
    height: 4rem;
    margin: auto;
    width: calc(100% + 5px);
    box-shadow: 0px 0px 5px 2px rgba(0, 0, 0, 0.3);
  }

  .container {
    width: 80%;
    margin: auto;
    position: relative;
  }
  .links {
    position: absolute;
    top: 50%;
    right: 0;
    transform: translateY(-50%);
    width: 50%;
    float: right;
    display: flex;
    justify-content: flex-end;
  }
  .links > button:not(.menu) {
    padding: 0 10px;
  }
  .menu {
    float: right;
    display: none;
    height: 3rem;
  }

  @media only screen and (max-width: 683px) {
    /* nav.navbar {
      width: 100%;
    } */
    .container {
      width: 92%;
    }
    .links {
      display: inherit;
    }
    .menu {
      display: initial;
    }
  }
  aside {
    position: absolute;
    right: 0;
    top: 0;
    width: 50vw;
    min-width: 300px;
    height: 100vh;
    z-index: 1000;
    background-color: var(--bg-dark);
    color: var(--accent);
    box-shadow: 10px 10px 10px 100vw rgba(0, 0, 0, 0.4);
    display: flex;
    flex-direction: column;
  }
  aside .close {
    font-size: 36px;
    color: var(--text-secondary);
    transform: translateX(-40%);
    margin: 0;
    padding: 0;
    border: 0;
    outline: 0;
    vertical-align: baseline;
    background: transparent;
  }

  @media only screen and (max-width: 1103px) {
    .links {
      width: calc(100vw - 200px);
    }
  }

  img:not([alt="svelte"]) {
    margin-top: -3px;
  }
</style>
