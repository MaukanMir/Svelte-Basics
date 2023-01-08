<script>
	// Imports Components here
	import Modal from "./Modeal.svelte";
    import AddPersonForm from "./AddPersonForm.svelte";


	
	let showModal = false;

	let people = [
		{ name: 'yoshi', beltColour: 'black', age: 25, id: 1 },
    	{ name: 'mario', beltColour: 'orange', age: 45, id: 2 },
    	{ name: 'luigi', beltColour: 'brown', age: 35, id: 3 }
	];

	const handleClick = (id) =>{
		people = people.filter(item => item.id !== id)
		console.log(people)
	}
	
	const toggleModal = () =>{
		showModal = !showModal;
	}

	const addPerson = (e) =>{
        const person = e.detail;
		people = [person, ...people]

		showModal = false;
    }
</script>

<Modal {showModal} on:click={toggleModal}>
<AddPersonForm on:addPerson={addPerson} />

</Modal>



<main>
	<button on:click={toggleModal}>Open Modal</button>
{#each people as person (person.id)}
<div>
	<h4>{person.name}</h4>
	<p>{person.beltColour}</p>
	{#if person.beltColour === "black"}
	<p> <strong>Black Belt</strong></p>
	{/if}
	<p>{person.age}</p>
	<button on:click ={() =>handleClick(person.id)}>Delete Person</button>
</div>
{:else}
<p>There are no people to show</p>
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