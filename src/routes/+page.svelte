<script>
	import { onMount } from 'svelte';
	import { baseUrl } from '../constants/baseUrl';
	import { writable } from 'svelte/store';

	/**
	 * @type {any[]}
	 */
	let data = [];

	onMount(async () => {
		const res = await fetch(`${baseUrl}/holidaze/venues`);
		data = await res.json();
		console.log(data);
	});
</script>

<h1>Welcome To Holidaze</h1>
<div>
	{#each data as venue}
		<div>
			<h2>{venue.name}</h2>
			<p>{venue.description}</p>
			<p>{venue.price}</p>
			<h3>Included</h3>
			<ul>
				{#each Object.entries(venue.meta) as [key, value]}
					{#if value}
						<li>{key}</li>
					{/if}
				{/each}
			</ul>
			<p>{venue.address}</p>
			<p>{venue.zip}</p>
			<p>{venue.city}</p>
			<p>{venue.country}</p>
		</div>
	{/each}
</div>
<p><a href="/about">About my site</a></p>
<p><a href="/blog/hello-world">Hello World</a></p>
