
<script>
import Header from "./UI/Header.svelte";
	import MeetupGrid from "./Meetups/MeetupGrid.svelte";
	import EditMeetup from "./Meetups/EditMeetup.svelte";
	import Button from "./UI/Button.svelte";
	
	let meetups = [
		{
			id: "m1",
			title: "COding camp",
			subtitle: "Coding learnt the easy way",
			description:
				"In this meetup we have experts to teach you to code well",
			imageUrl:
				"https://cdn.pixabay.com/photo/2017/08/30/01/05/milky-way-2695569__340.jpg",
			address: "21 Park street,Chennai",
			email: "test@code.com",
			isFavorite: false
		},
		{
			id: "m2",
			title: "COding camp 2",
			subtitle: "Coding community for everyone",
			description:
				"In this meetup we have experts to teach you to code well",
			imageUrl:
				"https://cdn.pixabay.com/photo/2017/08/30/01/05/milky-way-2695569__340.jpg",
			address: "21 Hal street,NY",
			email: "testmail@code.com",
			isFavorite:false
		},
	];
	let editmode;

	function addMeetUp(event){
		const newMeetup = {
			id:Math.random().toString(),
			title:event.detail.title, 
			subtitle:event.detail.subtitle,
			description:event.detail.description,
			imageUrl:event.detail.imageUrl,
			email:event.detail.email,
			address:event.detail.address
		};
		meetups=[newMeetup,...meetups];
		editmode=null;
	}
    
	function cancelEdit(){
		editmode=null;
	}

	function toggleFavorite(event){
       const id = event.detail;
	   const updatedMeetup = {...meetups.find(m=> m.id=== id)};
	   updatedMeetup.isFavorite = !updatedMeetup.isFavorite; 
	   const meetupIndex = meetups.findIndex(m=> m.id=== id);
	   const updatedMeetups =[...meetups];
	   updatedMeetups[meetupIndex]= updatedMeetup;
	   meetups= updatedMeetups;
	}

</script>

<Header />

<main>
	<div class="meetup-controls">
		<Button on:click={()=> (editmode='add')}>New meetup</Button>
	</div>
	{#if editmode==="add"}
		<EditMeetup on:save={addMeetUp} on:cancel={cancelEdit}/>
	{/if}
	<MeetupGrid {meetups} on:toggle-favorite={toggleFavorite}/>
</main>

<style>
	main {
		margin-top: 5rem;
	}
	.meetup-controls{
		margin: 1rem;
	}
	
</style>