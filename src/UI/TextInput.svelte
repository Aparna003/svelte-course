<script>
    export let controlType=null;
    export let id;
    export let labelName;
    export let rows=null;
    export let value;
    export let type="text";
</script>

<style>
    label{
        display: block;
        margin-bottom: 0.5rem;
        width: 100%;
    }
    .form-control {
        padding: 0.5rem 0;
        width: 100%;
        margin: 0.25rem 0;
    }
</style>
<div class="form-control">
    <label for="{id}">{labelName}</label>
{#if controlType==='textarea'}
    <textarea rows={rows} id="description" value={value} on:input />
{:else}
    <input type="{type}" id="title" value={value} on:input />
{/if}
</div>