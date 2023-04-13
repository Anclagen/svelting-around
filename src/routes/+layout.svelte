<script>
	let loggedIn = true;
	let user = null;

	const logout = () => {
		loggedIn = false;
		user = null;
	};
</script>

<nav>
	<a href="/">Home</a>
	<a href="/venues">Venues</a>
	<a href="/about">About</a>
	<a href="/contact">Contact</a>
	{#if loggedIn}
		<a href="/profile">Profile</a>
		<a on:click={logout} href="/">Logout</a>
	{:else}
		<a href="/login">Login</a>
		<a href="/register">Signup</a>
	{/if}
</nav>

<slot />

<footer>
	<p>©2023 - Holidaze</p>
	<p>Created by Alexander Barrett</p>
</footer>

<style>
	nav {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1rem;
	}

	nav a {
		color: #000;
		text-decoration: none;
	}

	nav a:hover {
		color: #000;
		text-decoration: underline;
	}

	footer {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1rem;
	}

	footer p {
		color: #000;
		text-decoration: none;
	}
</style>
