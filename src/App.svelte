<script>
	import Modal from './Modal.svelte';
	let people = [
		{name: 'RJay', beltColor: 'black', age: 24, id: 1},
		{name: 'Sudhanshu', beltColor: 'orange', age: 26, id: 2},
		{name: 'Prabh', beltColor: 'brown', age: 25, id: 3}
	];

	const handleCLick = (id) => {
		people = people.filter((person) => person.id != id);
	}

	setTimeout(() => {
		message = "Value Changed!!!!";
	}, 5000);

	let message = "Hey, I'm a prop value.";

</script>

<Modal message={message}/>
<main>
	{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			{#if person.beltColor === 'black'}
			<p><strong>Master Ninja</strong></p>
			{/if}
			<p>{person.age} years old, {person.beltColor} belt.</p>
			<button on:click={() => handleCLick(person.id) }>Delete</button>
		</div>
		{:else}
			<p>There are no people to show..</p>
	{/each}
</main> 

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>