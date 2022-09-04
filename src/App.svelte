<script>
	export let name;
	let firstname='martin'
	let lastname='mashalov'
	let color='blue'
	let visible_text = false 

	// define a list of users
	let users = [
		{id: "1", name: 'Bob'}, 
		{id: "2", name: 'Mary'}, 
		{id: "3", name: 'Sarah'}
	]

	// create dynamic variable 
	$: fullname = firstname + ' ' + lastname 

	const toggle = () => {
		if (color == 'blue') {
			color = 'red'
		}
		else if (color == 'red') {
			color = 'blue'
		}
		visible_text = !visible_text; // opposite of visible_text value 
		users = [...users, {id: 4, name: firstname}]
	}

</script>

<main>
	<h1 style="color: {color}">Hello {fullname}!</h1>
	{#if visible_text}
		<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	{:else} 
		<p>Hit the button for a surprise</p>
	{/if}
	<button on:click={toggle}>Click Me!</button>

	<!-- display list of users--> 
	{#each users as user (user.id)} 
		<h3>{user.id}: {user.name}</h3>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>