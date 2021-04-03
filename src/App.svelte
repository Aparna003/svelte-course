<script>
	import ContactCard from "./ContactCard.svelte";
	export let userName;
	let jobTitle="";
	let description="";
	let userImage="https://source.unsplash.com/random";
    let formState='empty';
	let createdContact=[];
	function addContact(){
		if(userName.trim().length==0 ||
		jobTitle.trim().length==0 ||
		userImage.trim().length==0 ||
		description.trim().length==0
		){
           formState="invalid";
		   return;
		}
		createdContact= [
			...createdContact,
			{
			userName,
			jobTitle,
			userImage,
			description
		}];

		formState='done';
		}
</script>

<div class="form">
	<div class="form-control">
      <label for="userName">User Name</label>
	  <input type="text" bind:value={userName} id="userName" />
	</div>
	<div class="form-control">
		<label for="jobTitle">Job title</label>
		<input type="text" bind:value={jobTitle} id="jobTitle" />
	</div>
	<div class="form-control">
		<label for="image">Image URL</label>
		<input type="text" bind:value={userImage} id="image" />
	</div>
	<div class="form-control">
		<label for="desc">Description</label>
		<textarea rows="3" bind:value={description} id="desc" />
	</div>
</div>
<button on:click="{addContact}">Add contact card</button>


{#if formState==="invalid"}
<p>Invalid input</p>
{:else}
<p>Please fill all the fields and submit!</p>
{/if}
{#each createdContact as contact,i}
<h2># {i+1}</h2>
<!-- <ContactCard userName={contact.userName} 
jobTitle={contact.title} 
description={contact.des} 
userImage={contact.image}/> -->
<ContactCard {...contact}/>
{:else}
<p>Start adding by making contacts!</p>
{/each}


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
