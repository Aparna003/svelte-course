
<script>
    import {createEventDispatcher} from 'svelte';
    import TextInput from "../UI/TextInput.svelte";
    import Button from "../UI/Button.svelte";
    import Modal from '../UI/Modal.svelte';

    let title='';
	let subtitle='';
	let address='';
	let description=''; 
	let imageUrl='';
	let email='';
	
    const dispatch = createEventDispatcher();
    function submitForm(){
        dispatch('save',{
            title:title,
            subtitle:subtitle,
            address:address,
            email:email,
            description:description,
            imageUrl:imageUrl
        })
    }

    function cancel(){
        dispatch('cancel');
    }
</script>
<style>
    form{
		width: 100%;
	}
</style>

<Modal title="Edit Meetup Data" on:cancel>
    <form  on:cancel>
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
        </form>
        <div slot="footer">
            <Button type="button" mode="outline" on:click={cancel}> Cancel</Button>
            <Button type="button" on:click={submitForm}> Save</Button>
        </div>
</Modal>