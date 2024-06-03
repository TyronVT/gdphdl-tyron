<script>
    export let titleName;
    export let description;
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');
    * {
        font-family: 'Outfit';
    }

    .title-container {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        width: 100vw;
        height: 20%;
        background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.7)), url("../lib/titlepage_background.png");
        background-size: auto;
        background-position: center;
        padding-top: 5%;
        padding-bottom: 5%;
    }

    h1, p {
        color: white; 
    }
</style>

<div class="title-container">
    <h1>{titleName}</h1>
    <p>{description}</p>
</div>