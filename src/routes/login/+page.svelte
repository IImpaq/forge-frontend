<script lang="ts">
	const forgotPassword = () => {

	};

	const login = () => {

	};
</script>

<section class="register">
	<div class="title" >
		<h1>Login</h1>
		<h2>Use your existing account</h2>
	</div>
	<div class="content">
		<form>
			<div class="group">
				<label for="lastname">Email</label>
				<input type="email" name="email" placeholder="placeholder@domain.com"/>
			</div>

			<div class="group">
				<label for="lastname">Password</label>
				<input type="password" name="password" placeholder="Your Password"/>
			</div>

			<div class="group-nav">
				<button class="btn-prev" on:click={forgotPassword}>Forgot Password</button>
				<button class="btn-next" on:click={login}>Login</button>
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
			background-color: var(--bg-dark);
			display: flex;
			align-items: center;
			justify-content: center;
			gap: 5vw;
			padding: 5rem;
			border-radius: 1.5rem;

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
						color: var(--text-light);
					}

					input, textarea {
						border: none;
						background-color: var(--bg-dark);
						padding: 1rem 1rem 1rem 1rem;
						color: var(--text-light);
						font-family: Lato, sans-serif;
						font-size: 0.9rem;
						border-bottom: 0.1rem solid var(--text-light);
					}
				}

				.group-nav {
					display: flex;
					flex-direction: row;
					justify-content: flex-start;
					gap: 1rem;

					.btn-prev {
						margin: 0;
						padding: 0.75rem 1rem 0.75rem 1rem;
						font-size: 0.9rem;
						background-color: var(--bg-dark);
						color: var(--text-light);
						cursor: pointer;
						border: none;
						border-radius: 0.5rem;
					}

					.btn-next {
						margin: 0;
						padding: 0.75rem 2rem 0.75rem 2rem;
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