
<script>
import Header from "./UI/Header.svelte";
	import MeetupGrid from "./Meetups/MeetupGrid.svelte";
	import Button from './UI/Button.svelte';
    import TextInput from './UI/TextInput.svelte';
	let title='';
	let subtitle='';
	let address='';
	let description=''; 
	let imageUrl='';
	let email='';
	
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
	function addMeetUp(){
		const newMeetup = {
			id:Math.random().toString(),
			title,
			subtitle,
			description,
			imageUrl,
			email,
			address
		};
		meetups=[newMeetup,...meetups];
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
	<form on:submit|preventDefault="{addMeetUp}">
		<TextInput id="title" labelName="Title" value={title} 
		  on:input="{event => title=event.target.value }" />
		<TextInput id="subtitle" labelName="Subtitle" value={subtitle} 
	      on:input="{event => subtitle= event.target.value }" />
		<TextInput id="address" labelName="Address" value={address} 
		  on:input="{event => address= event.target.value }" />
		<TextInput id="imageUrl" labelName="imageUrl" value={imageUrl} 
		  on:input="{event => imageUrl=event.target.value }" />
		<TextInput id="email" labelName="Email" value={email} 
		 type="email" on:input="{event =>email= event.target.value }" />
		<TextInput id="descripton" rows="3" controlType="textarea" labelName="Description" value={description} 
	 	on:input="{event => description=event.target.value }" />

		<Button type="submit" caption="save"/>

	</form>
	<MeetupGrid {meetups} on:toggle-favorite={toggleFavorite}/>
</main>

<style>
	main {
		margin-top: 5rem;
	}
	form{
		width: 30rem;
		max-width: 90%;
		margin: auto;
	}
</style>