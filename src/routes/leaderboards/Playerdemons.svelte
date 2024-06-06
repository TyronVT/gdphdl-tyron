<script>
    import { fade, slide } from 'svelte/transition';
    export let demonData;
    let selectedCategory = "Main Demons";
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');
    h1, p {
        color: white;
        text-align: center;
    }

    h1 {
        font-size: 2rem;
    }

    p {
        font-size: 1rem;
    }

    .demons-container {
        padding: 1rem;
        text-align: center;
    }

    .demon-selector {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 1vw;
    }

    .demon-selector > button {
        background-color: black;
        color: white;
        padding: 1rem;
        border: none;
        border-bottom: 1px solid white;
        font-size: 1rem;
    }

    @media (max-width: 480px) {
        h1, p {
            color: white;
            text-align: center;
        }

        h1 {
            font-size: 5vw;
        }

        p {
            font-size: 3vw;
        }

        .demons-container {
            padding: 1rem;
            text-align: center;
        }

        .demon-selector {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 1vw;
        }

        .demon-selector > button {
            background-color: black;
            color: white;
            padding: 2vw;
            border: none;
            border-bottom: 1px solid white;
            font-size: 2.5vw;
        }
    }

</style>

<div class="player-demons">
    {#await demonData}
        <p transition:slide|global="{{duration: 200, delay: 10}}">Fetching Player Demons ...</p>
    {:then data}
        <div class="demon-selector">
            <button on:click={() => selectedCategory = "Main Demons"} transition:slide|global="{{duration: 200, delay: 10}}">Main Demons</button>
            <button on:click={() => selectedCategory = "Extended Demons"} transition:slide|global="{{duration: 200, delay: 10}}">Extended Demons</button>
            <button on:click={() => selectedCategory = "Legacy List"} transition:slide|global="{{duration: 200, delay: 10}}">Legacy List</button>
            <button on:click={() => selectedCategory = "In Progress"} transition:slide|global="{{duration: 200, delay: 10}}">In Progress</button>
        </div>

        <div class="demons-container">
            <h1 transition:slide|global="{{duration: 200, delay: 10}}">{selectedCategory}</h1>
            {#each data[selectedCategory] as demon, index (demon)}
                {#if selectedCategory != "In Progress"}
                    <p transition:slide|global="{{duration: 200, delay: index*10}}">{demon.level_name}</p>
                {:else}
                    <p transition:slide|global="{{duration: 200, delay: index*10}}">{demon.level_name}, {demon.percent_completed}%</p>
                {/if}
            {/each}
        </div>
    {:catch error}
        <p>error.message</p>
    {/await}
</div>