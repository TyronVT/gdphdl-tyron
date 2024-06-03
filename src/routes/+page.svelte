<script>
    import Titlepage from "./Titlepage.svelte";
    import Announcement from "./Announcement.svelte";
    import Comingsoon from "./Comingsoon.svelte";

</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');
    * {
        font-family: 'Outfit';
    }

    /* .title-supporting-text {
        text-align: center;
        font-size: 1.7rem;
    } */

    .content-container {
        display: flex;
    }

</style>

<Titlepage titleName="GDPH Demonlist" description="Welcome to the GDPH Demon List!" />
<!-- <h1 class="title-supporting-text">Home of the official GD Philippines Demon List!</h1> -->

<div class="content-container">
    <Comingsoon />
    <Announcement />
</div>