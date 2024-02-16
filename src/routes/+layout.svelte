<script>
	import { fade } from "svelte/transition"

	import Navbar from "$lib/components/Navbar.svelte"

	export let data;
</script>


<Navbar />

{#key data.currentRoute}
	<main in:fade={{ duration: 100, delay: 100 }} out:fade={{ duration: 100 }}>
		<slot />
	</main>
{/key}

<style lang="scss">
  @font-face {
    font-family: "Lato";
    src: url("$lib/assets/fonts/Lato/Lato-Regular.ttf");
    font-weight: 400;
    font-style: normal;
    font-display: swap;
  }

  @font-face {
    font-family: "Lato";
    src: url("$lib/assets/fonts/Lato/Lato-Bold.ttf");
    font-weight: 500;
    font-style: normal;
    font-display: swap;
  }

  @font-face {
    font-family: "Lato";
    src: url("$lib/assets/fonts/Lato/Lato-Black.ttf");
    font-weight: 600;
    font-style: normal;
    font-display: swap;
  }

  * {
    font-family: "Lato", "Times New Roman", sans-serif;
  }

  body {
    background: var(--bg-light);
    color: var(--text-dark);
    padding: 0;
    margin: 0;
  }

  main {
    padding: 0;
    margin: 0;
    width: 100%;
  }

  :global(:root) {
    --bg-light: #FFF;
    --bg-dark: #101010;
    --bg-semi: #EDEDED;

    --text-dark: #101010;
    --text-light: #EEE;
    --text-semi: #707070;

    --box-shadow: rgba(0, 0, 0, 0.24);
  }

  :global(body.dark-mode) {
    --bg-light: #101010;
    --bg-dark: #FFF;
    --bg-semi: #242424;

    --text-dark: #EEE;
    --text-light: #101010;
    --text-semi: #AAA;

    --box-shadow: rgba(255, 255, 255, 0.24);
  }
</style>
