<script>
    export let userName;
    export let jobTitle;
    export let description;
    export let userImage;
    const initialName= userName;
</script>



<style scoped>
.contact-card{
    box-shadow:  0 2px 8px rgba(0,0,0,0.26);
    max-width: 30rem;
    border-radius: 5px;
    margin: 1rem 0;
}
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.thumb{
    width:33%;
    height: 100%;
   
}
.thumb-placeholder{
    background: #ccc;
}
img{
    width: 100%;
    height: 100%;
    object-fit: cover;
}
.user-data{
    width: 80%;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
h1{
    font-size: 1.25rem;
    font-family: "Roboto Slab",sans-serif;
}
h2{
    font-size: 1rem;
    font-weight: normal;
    color: #5a5a5a;
}
.desc{
    border-top:1px solid #ccc;
    padding: 1rem;
}
</style>

<div class="contact-card">
    <header>
        <div class="thumb" class:thumb-placeholder={!userImage}>
            <img src="{userImage}" alt="{userName}" />
        </div>
        <div class="user-data">
            <h1>{userName}/ {initialName}</h1>
            <h2>{jobTitle}</h2>
        </div>
    </header>
    <div>
        <p class="desc">
             <!-- {@html description}  html text -->
             {description}
        </p>
    </div>
</div>
