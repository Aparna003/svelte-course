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
</script>

<Header />

<main>
	<form on:submit|preventDefault="{addMeetUp}">
		<TextInput id="title" labelName="Title" value={title} 
		 type="text" on:input="{event => title=event.target.value }" />
		<TextInput id="subtitle" labelName="Subtitle" value={subtitle} 
	     type="text" on:input="{event => subtitle= event.target.value }" />
		<TextInput id="address" labelName="Address" value={address} 
		 type="text" on:input="{event => address= event.target.value }" />
		<TextInput id="imageUrl" labelName="imageUrl" value={imageUrl} 
		 type="text" on:input="{event => imageUrl=event.target.value }" />
		<TextInput id="email" labelName="Email" value={email} 
		 type="email" on:input="{event =>email= event.target.value }" />
		<TextInput id="descripton" rows="3" controlType="textarea" labelName="Description" value={description} 
	 	on:input="{event => description=event.target.value }" />
		
		<Button type="submit" caption="save"/>

	</form>
	<MeetupGrid {meetups} />
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
