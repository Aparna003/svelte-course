<script>
	import ContactCard from "./ContactCard.svelte";
	export let name;
	let age = 20;
	let title="";
	let des="";
	let image="https://source.unsplash.com/random";
    let formState='empty';
	// // let uppercaseName; is not required
	// $: uppercaseName = name.toUpperCase();
	// $: console.log(name);
	// function increaseAge() {
	// 	age += 1;
	// }
	// $: if (name === "Bangy") {
	// 	age=19;
	// }
	// function changeName() {
	// 	name = "Bangy"; // even though name is changed, the uppercase is still maintained
	// }
	// function nameInput(event){
	// const newName = event.target.value;
	// name=newName;
	// }
	function addContact(){
		if(name.trim().length==0 ||
		title.trim().length==0 ||
		image.trim().length==0 ||
		des.trim().length==0
		){
           formState="invalid";
		   return;
		}
		formState='done';
	}
</script>

<div class="form">
	<div class="form-control">
      <label for="userName">User Name</label>
	  <input type="text" bind:value={name} id="userName" />
	</div>
	<div class="form-control">
		<label for="userName">Job title</label>
		<input type="text" bind:value={title} id="jobTitle" />
	</div>
	<div class="form-control">
		<label for="userName">Image URL</label>
		<input type="text" bind:value={image} id="image" />
	</div>
	<div class="form-control">
		<label for="userName">Description</label>
		<textarea rows="3" type="text" bind:value={des} id="desc" />
	</div>
</div>
<button on:click="{addContact}">Add contact card</button>
{#if formState==="done"
}
<ContactCard userName={name} 
jobTitle={title} 
description={des} 
userImage={image}/>
{:else if formState==="invalid"}
<p>Invalid input</p>
{:else}
<p>Please fill all the fields and submit!</p>
<!-- {#if formState==="invalid"} -->
{/if}
<style>
	.form {
		width: 30rem;
		max-width: 100%;
	}
	button{
	background-color: #e40763;
	color: aliceblue;
	outline: none;
	border-radius: 0.5em;
	padding: 0.5rem;
	}
	
</style>
