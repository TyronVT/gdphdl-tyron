<script>
    import Titlepage from "../Titlepage.svelte";
    import DemonManager from "./DemonManager.svelte";

    export let data;
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');

    * {
        font-family: 'Outfit';
        color: white;
        padding: 0;
        margin: 0;
    }
    :global(body) {
        margin: 0;
        padding: 0;
        overflow-x: hidden;
    }
    .content-container {
        width: 100vw;
        height: max-content;
        background-color: black;
    }
    button {
        background-color: black;
        padding: 1rem;
        font-size: 1vw;
        border: none;
        border-bottom: 2px solid white;
    }
    .admin-panel {
        display: flex;
        justify-content: center;
        gap: 1vw;
    }

</style>

<Titlepage titleName="Admin Panel" description="Manage Players and Demons here." />
<div class="content-container">
    {#if !data.user}
        <h1>You do not have access to this resource.</h1>
    {:else}
        <div class="admin-panel">
            <button>Manage Demons</button>
            <button>Manage Player</button>
            <button>Add Player</button>
            <form action="../logout" method="POST">
                <button type="submit">Logout</button>
            </form>
        </div>
        <div class="manage-demons">
            <DemonManager/>
        </div>
    {/if}
</div>
