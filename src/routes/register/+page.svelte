<script lang="ts">
	import { ArrowRightCircleIcon } from '@indaco/svelte-iconoir/arrow-right-circle';

	enum State {
		PERSONAL = 0,
		RESIDENCE = 1,
		ACCOUNT = 2,
		FINALIZE = 3
	}

	let currentState: State = State.PERSONAL;

	const prevState = () => {
		currentState = currentState - 1;
	};
	const nextState = () => {
		currentState = currentState + 1;
	};
</script>

<section class="register">
	<div class="title" >
		<h1>Register</h1>
		<h2>Create a new account</h2>
	</div>
	<div class="content">
		<div class="progress">
			<div class="section">
				<ArrowRightCircleIcon class="" size="sm" />
				{#if currentState === State.PERSONAL}
					<p class="bold">Personal</p>
				{:else}
					<p>Personal</p>
				{/if}
			</div>
			<div class="section">
				<ArrowRightCircleIcon class="" size="sm" />
				{#if currentState === State.RESIDENCE}
					<p class="bold">Residence</p>
				{:else}
					<p>Residence</p>
				{/if}
			</div>
			<div class="section">
				<ArrowRightCircleIcon class="" size="sm" />
				{#if currentState === State.ACCOUNT}
					<p class="bold">Account</p>
				{:else}
					<p>Account</p>
				{/if}
			</div>
			<div class="section">
				<ArrowRightCircleIcon class="" size="sm" />
				{#if currentState === State.FINALIZE}
					<p class="bold">Finalize</p>
				{:else}
					<p>Finalize</p>
				{/if}
			</div>
		</div>

		<form>
			{#if currentState === State.PERSONAL}
				<div class="description">
					<h1>First, we need to get to know you</h1>
					<p>Please make sure to only enter valid information.</p>
				</div>

				<div class="group">
					<label for="lastname">Name</label>
					<div class="subgroup">
						<input type="text" name="firstname" placeholder="First Name"/>
						<input type="text" name="lastname" placeholder="Last Name"/>
					</div>
				</div>

				<div class="group">
					<label for="day">Birthday</label>
					<div class="subgroup">
						<input type="number" name="day" placeholder="Day"/>
						<input type="number" name="month" placeholder="Month"/>
						<input type="number" name="year" placeholder="Year"/>
					</div>
				</div>
			{:else if currentState === State.RESIDENCE}
				<div class="description">
					<h1>Where are you from?</h1>
					<p>We need to know this information for regulatory purposes.</p>
				</div>

				<div class="group">
					<label for="country">Country</label>
					<input type="text" name="country" placeholder="Austria"/>
				</div>
			{:else if currentState === State.ACCOUNT}
				<div class="description">
					<h1>Now, let's setup your access</h1>
					<p>Enter your email address in case we need to contact you, but also to log in with your password.</p>
				</div>

				<div class="group">
					<label for="email">Email</label>
					<input type="email" name="email" placeholder="your@domain.com"/>
				</div>

				<div class="group">
					<label for="password">Password</label>
					<input type="password" name="password" placeholder="secret_password"/>
				</div>
			{:else if currentState === State.FINALIZE}
				<div class="description">
					<h1>Finally, the boring legal stuff</h1>
					<p>Accepting our terms of service as well as privacy policy is required to be able to use our services.</p>
				</div>

				<div class="group">
					<label for="email">Email</label>
					<input type="email" name="email" placeholder="your@domain.com"/>
				</div>

				<div class="group">
					<label for="password">Password</label>
					<input type="password" name="password" placeholder="secret_password"/>
				</div>
			{/if}

			<div class="group-nav">
				<button class="btn-prev" on:click={prevState}>Back</button>
				<button class="btn-next" on:click={nextState}>Next</button>
			</div>
		</form>
	</div>
</section>

<style lang="scss">
.register {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: min(10rem, 15vw) min(15rem, 5vw) min(10rem, 15vw) min(15rem, 5vw);
  gap: 5rem;

  .title {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    h1 {
      font-size: 3rem;
      font-weight: bold;
      padding: 0 0 0.2rem 0;
      margin: 0;
    }

    h2 {
      font-size: 1.1rem;
      color: var(--text-semi);
      padding: 0 0 1.1rem 0;
      margin: 0;
    }
  }

	.content {
		background: var(--bg-light);
		display: flex;
		align-items: center;
    justify-content: flex-start;
		gap: 5vw;
		width: 75vw;
		height: 25vh;

		.progress {
			display: flex;
			flex-direction: column;
      gap: 0rem;

			.section {
				display: flex;
				align-items: center;
				gap: 1rem;

				.bold {
					font-weight: bold;
				}
			}
		}

		form {
      display: flex;
			flex-direction: column;
			gap: 2rem;

			.description {
				display: flex;
				flex-direction: column;
				gap: 0;

				h1 {
					font-size: 2rem;
					line-height: 0;
				}

				p {
          font-size: 1.1rem;
					line-height: 0;
				}
			}

			.group {
				display: flex;
				flex-direction: column;

				.subgroup {
          display: flex;
          flex-direction: row;
				}

        label {
          padding: 0;
          margin: 0;
          font-size: 1.1rem;
          color: var(--text-dark);
        }

        input, textarea {
          border: none;
          background-color: var(--bg-light);
          padding: 1rem 1rem 1rem 1rem;
          color: var(--text-dark);
          font-family: Lato, sans-serif;
          font-size: 0.9rem;
          border-bottom: 0.1rem solid var(--text-dark);
        }
			}

			.group-nav {
				display: flex;
				flex-direction: row;
				justify-content: flex-start;
				gap: 1rem;

        .btn-prev {
          margin: 0;
          padding: 0.75rem 1.5rem 0.75rem 1.5rem;
          font-size: 0.9rem;
          background-color: var(--bg-semi);
          color: var(--text-dark);
          cursor: pointer;
          border: none;
          border-radius: 0.5rem;
        }

        .btn-next {
          margin: 0;
          padding: 0.75rem 1.5rem 0.75rem 1.5rem;
          font-size: 0.9rem;
          background-color: var(--cta-light);
          color: var(--text-dark);
          cursor: pointer;
          border: none;
          border-radius: 0.5rem;
        }
			}
		}
	}
}
</style>