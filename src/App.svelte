<script>
	export let name;
	let variableA = 'black';

	let firstName = 'Jimmy';
	let lastName = 'second Name';


	$: fullName = `${firstName}  ${lastName}`;

	const handleClick = () =>{
		variableA = 'red';
	}

	const handleInput = (e) =>{
		variableA = e.target.value;
	}

	let people = [
    { name: 'yoshi', beltColour: 'black', age: 25, id: 1 },
    { name: 'mario', beltColour: 'orange', age: 45, id: 2 },
    { name: 'luigi', beltColour: 'brown', age: 35, id: 3 }
  ];


  const handleClickLoop = (id) => {
    people = people.filter(person => person.id != id);
  };
</script>

<main>
	<h1>Hello {name}!</h1>
	<p style="color :{variableA}">selamat pagi {variableA}</p>
	<button on:click={handleClick}>belt update button</button>
	<!-- <input type="text" on:input={handleInput} value={variableA}/> -->
	
	<input type="text"  bind:value={variableA} />

	<!-- next lesson -->
	<p>{fullName} - {variableA}</p>
	<input type="text"  bind:value={firstName} />
	<input type="text"  bind:value={lastName} />
	<input type="text"  bind:value={variableA} />
	<br/>

	{#each people as person (person.id)}
		<div>
		<h4>{person.name}</h4>
		<p>{person.age} years old, {person.beltColour} belt.</p>
		<button on:click={() => handleClickLoop(person.id)}>delete</button>
		</div>
	{:else}
		<p>There are no people to show...</p>
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