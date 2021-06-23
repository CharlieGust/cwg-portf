<script>

  import Navbar from "./components/Navbar.svelte";
  import Home from "./routes/Home.svelte";
  import Sites from "./routes/Sites.svelte";
	import Skills from "./routes/Skills.svelte"
	import Kontakt from "./routes/Kontakt.svelte"

	import Transition from "./components/Transition.svelte"
  import { activeStore } from "./stores";
</script>

<Navbar />

<main>
  {#if $activeStore === "Home"}
		<Transition>
			<Home />
		</Transition>
  {:else if $activeStore === "Projekt"}
		<Transition>
			<Sites />
		</Transition>
	{:else if $activeStore === "Skills"}
		<Transition>
			<Skills />
		</Transition>
	{:else if $activeStore === "Kontakt"}
		<Transition>
			<Kontakt />
		</Transition>
  {/if}
</main>
<!--
<nav class="navbar">

	<a href="/#/" use:active exact style="font-size:3.5rem; margin-right: 20%;">hemma</a>
	<a href="/#/portfolio" use:active style="font-size:3.3rem; margin-right: 1rem">verken</a>
	<a href="/#/contacts" use:active style="font-size:4.5rem;">kontakt</a>
</nav>

<Route path="/"><h1>It is main page</h1></Route>
<Route path="/portfolio/*">
	<Route path="/">
			<h1>Portfolio introduction</h1>
			<nav>
					<a href="/#/portfolio/sites">Sites</a>
					<a href="/#/portfolio/photos">Photos</a>
			</nav>
	</Route>
	<Route path="/sites"><h1>Portfolio: Sites</h1> <Sites /></Route>
	<Route path="/photos"><h1>Portfolio: Photos</h1></Route>
</Route>
<Route path="/contacts"><Contacts /></Route> -->
