<script>
    import { fade, slide } from 'svelte/transition';
    export let demonData;
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');
    .player-demons {
        display: flex;
        gap: 2rem;
        justify-content: center;
    }

    h1, p {
        color: white;
    }

    h1 {
        font-size: 1.3rem;
    }

    .demons-container {
        padding: 1rem;
    }

    .separator {
        border-top: 3px solid #bbbb;
    }
</style>

<div class="player-demons">
    <div class="separator" transition:slide|global="{{duration: 500, delay: 0}}"></div>
    {#await demonData}
    <p>Fetching Player Demons ...</p>
    {:then data}
        <div class="demons-container">
            <h1 transition:slide>Main Demons</h1>
            {#each data["Main Demons"] as demon, index (demon)}
                <p transition:slide|global="{{duration: 200, delay: index*10}}">{demon.level_name}</p>
            {/each}
        </div>
        <div class="demons-container">
            <h1 transition:slide>Extended Demons</h1>
            {#each data["Extended Demons"] as demon, index (demon)}
                <p transition:slide|global="{{duration: 200, delay: index*20}}">{demon.level_name}</p>
            {/each}
        </div>
        <div class="demons-container">
            <h1 transition:slide>Legacy Demons</h1>
            {#each data["Legacy List"] as demon, index (demon)}
                <p transition:slide|global="{{duration: 200, delay: index*20}}">{demon.level_name}</p>
            {/each}
        </div>
        <div class="demons-container">
            <h1 transition:slide>In Progress</h1>
            {#each data["In Progress"] as demon, index (demon)}
                <p transition:slide|global="{{duration: 200, delay: index*20}}">{demon.level_name} {demon.percent_completed}%</p>
            {/each}
        </div>
    {:catch error}
        <p>error.message</p>
    {/await}
</div>