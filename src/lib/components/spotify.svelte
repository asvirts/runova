<script>
	let data = null;
	let error = null;

	// Function to fetch data from the API
	async function fetchData() {
		try {
			const response = await fetch('https://api.spotify.com/v1/search?q=relientk&type=artist');
			if (!response.ok) {
				throw new Error('Network response was not ok');
			}
			data = await response.json();
		} catch (err) {
			error = err.message;
		}
	}

	// Call the fetchData function when the component is mounted
	fetchData();
</script>

<template>
	{#if error}
		<p>Error: {error}</p>
	{:else if !data}
		<p>Loading...</p>
	{:else}
		<pre>{data}</pre>
	{/if}
</template>
