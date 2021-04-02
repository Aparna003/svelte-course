<script>
	import ContactCard from "./ContactCard.svelte";
	export let name;
	let age = 20;

	// let uppercaseName; is not required
	$: uppercaseName = name.toUpperCase();
	$: console.log(name);
	function increaseAge() {
		age += 1;
	}
	$: if (name === "Bangy") {
		age=19;
	}
	function changeName() {
		name = "Bangy"; // even though name is changed, the uppercase is still maintained
	}
	function nameInput(event){
	const newName = event.target.value;
	name=newName;
	}
</script>

<main>
	<h1>Hello {uppercaseName}!<br /> My age is {age}</h1>
	<!-- "" can and neednt be used for attributes if {} are used -->
	<button on:click={increaseAge}>Change Age</button>
	<!-- <input type="text" value="{name}" on:input={nameInput} /> -->
  
	<!-- 2 way bind shortcut -->
	  <input type="text" bind:value="{name}" />
      <ContactCard/>
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
		/* text-transform: uppercase; */
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
