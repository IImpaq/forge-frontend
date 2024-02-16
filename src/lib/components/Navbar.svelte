<script>
	import Hamburger from '$lib/components/Hamburger.svelte';
	import { MoreVertIcon } from '@indaco/svelte-iconoir/more-vert';

	let opened = false;
	let navbarWidth;

	let onClick = () => opened = !opened;
</script>

<header bind:clientWidth={navbarWidth}>
	{#if navbarWidth < 768}
		<div class="mobile">
			<a class="logo" href="/">Forge</a>
			<Hamburger size="7.5vw" {opened} {onClick}/>
		</div>
	{:else}
		<div class="desktop">
			<a class="logo" href="/">Forge</a>
		</div>
	{/if}

	{#if opened || navbarWidth >= 768}
		<nav class="navbar">
			<ul class="links">
				<li><a class="link" href="/private" on:click="{onClick}">Private</a></li>
				<li><a class="link" href="/business" on:click="{onClick}">Business</a></li>
				<li><a class="link" href="/about" on:click="{onClick}">About</a></li>
			</ul>
			<ul class="organisational">
				<MoreVertIcon class="" size="xs" />
				<li><a class="btn-login" href="/login" on:click="{onClick}">Login</a></li>
				<li><a class="btn-register" href="/register" on:click="{onClick}">Register</a></li>
			</ul>
		</nav>
	{/if}
</header>

<style lang="scss">
  header {
    padding: min(2rem, 5vw) min(4rem, 10vw);
    background: var(--bg-light);
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
    color: var(--text-dark);

    .mobile {
      width: 100%;
      display: flex;
      flex-direction: row;
      justify-content: space-between;

      .logo {
        font-weight: bold;
        text-decoration: none;
        color: inherit;
        font-size: 2rem;
      }
    }

    .desktop {
      .logo {
        font-weight: bold;
        text-decoration: none;
        color: inherit;
        font-size: 2rem;
      }
    }

    .navbar {
			display: flex;

      .links {
        margin: 0;
        list-style-type: none;
        display: flex;
        align-items: center;
        gap: 2rem;

        li {
          .link {
            text-decoration: none;
            color: inherit;
          }
        }
      }

      .organisational {
        margin: 0;
        list-style-type: none;
        display: flex;
        align-items: center;
        gap: 0.5rem;

        li {
					a {
            text-decoration: none;
            color: inherit;
					}

          .btn-login {
            background: var(--bg-semi);
            padding: 0.75rem 1.5rem;
            border-style: none;
            border-radius: 0.5rem;
						cursor: pointer;
          }

          .btn-register {
            background: var(--cta-dark);
            padding: 0.75rem 1.5rem;
            border-style: none;
            border-radius: 0.5rem;
            color: var(--text-light);
          }
        }
      }
    }
  }

  @media (max-width: 782px) {
    header {
      flex-direction: column;
      justify-content: center;
      align-items: center;
      gap: 1rem;

      .navbar {
        ul {
          gap: 1rem;
          padding: 0;
          flex-direction: column;
        }
      }
    }
  }
</style>
