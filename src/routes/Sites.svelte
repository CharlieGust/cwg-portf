<script>
  import { projectStore, activeStore } from "../stores";
  import Project from "../components/Project.svelte";
  import slideAnimate from "../slideAnimate2";
  // let open = false;

  // const toggleOpen = () => (open = !open);

  // let yes = false;

  const projs = [
    {
      title: "Dota Picker",
      desc: "Svårt att bestämma vilken hero du ska spela? Du hamnar i gamla vanor och det slutar med att du spelar pudge för tredje gången i rad. Känner du igen dig? Misstro ej Dota picker är en app för dig, med ett enkelt knapptryck väljer Dota picker en hero åt dig PLUS vilka abillities och stats heron har! Så vad väntar du på? KLICKA LOSS ",
      src: "./images/dotapicker1.png",
    },
    {
      title: "Pipenv tasks",
      desc: "sadadssd",
      src: "./images/dotapicker1.png",
    },
  ];
</script>

<h1>{$activeStore}</h1>
<!-- {#if yes}
<button on:click={toggleOpen}>Toggle</button>
{/if} -->

<div class="outerDiv">
  {#if $projectStore === null}
    {#each projs as pro, i}
    <div class="innerDiv">
    <h2>{pro.title}</h2>
      <section>
        <nav>
          <p>{pro.desc}</p>
          <button class="transparent" on:click={() => ($projectStore = i)}>
            SHOW MORE
          </button>
        </nav>
      </section>
    </div>
    {/each}
  {:else}
    <Project {...projs[$projectStore]} />
  {/if}
</div>

<!-- <section style="background-image: url('{pro.src}');"> -->

<!-- <label>
      <input type="checkbox" bind:checked={yes}>
      I want this one!
    </label> -->
<style>


  h2 {
    /* position: absolute; */
    max-width: 90%;
    font-size: 2em;
    /* top: 10%;
    left: 10%; */
    color: white;
    margin-bottom: 10px;
    border-bottom: 2px solid white;
    /* margin-right: 2%; */
  }
  section {
    margin-bottom: 20px;

    /* position: relative;
    height: 50vh;
    min-width: 60%;
    margin: 10px;
    background-position: 0 50%;
    border-radius: 14px;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
    display: inline-block;
    white-space: normal; */
    /* border: 2px solid yellow; */
  }
  p {
    margin-bottom: 10px;
  }
  button {
    /* border: 1px solid var(--accent); */
    color: var(--accent);
  }
      /*
  nav {
 width: 100%;
    position: absolute;
    bottom: 5%;
    margin: auto;
    display: flex;
    justify-content: space-evenly; */
    /* margin-right: 20px; */
  /* } */

  /*
   <!-- <h2>{pro.title}</h2>

      <section
        style="background-image: linear-gradient(rgba(0,0,0, 0.6),rgba(0,0,0,
      0.6)"
      >
        <nav>
          <button class="transparent" on:click={() => ($projectStore = i)}>
            SHOW MORE
          </button>
        </nav>
        <p>{pro.desc}</p>
      </section> -->
div {
    display: grid;
    grid-template-columns: repeat(auto-fit);
  }

  @media only screen and (max-width: 683px) {
    div {
      overflow-x: scroll;
      white-space: nowrap;
      display: block;
    }
  }

  section {
    position: relative;
    height: 20vh;
    min-width: 70%;
    margin: 10px;
    border-radius: 14px;
    display: inline-block;
  }

  h2 {
    color: var(--accent);
    font-size: 4vh;
  }
  p {
    color: white;
    padding: 10px 0;
    width: 100%;
  }

  button {
    width: 45%;
    color: white;
    border-color: white;
  }
  nav {
    width: 100%;
    position: absolute;
    bottom: 5%;
    margin: auto;
    display: flex;
    justify-content: space-evenly;
  } */
</style>
