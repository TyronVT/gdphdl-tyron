<script lang="ts">
    import Pocketbase from "pocketbase";
    import Titlepage from "../Titlepage.svelte";
    import Level from "./Level.svelte";
    const pb = new Pocketbase('https://gdph-demons.pockethost.io');
    async function getLevels(): Promise<Array<any>> {
        const records = await pb.collection("level_ranks_and_points").getFullList();
        return records;
    }
</script>

<style>
    :global(body) {
        margin: 0;
        padding: 0;
        overflow-x: hidden;
    }

    .levels-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        background-color: black;
        width: 100vw;
    }

    p {
        color: white;
    }

    .filler-black {
        width: 100%;
        background-color: black;
        height: 100%;
        position: absolute;
        z-index: -1;
        padding: 1rem;
    }
</style>

<Titlepage titleName="Top 150 List" description="Demon List Leaderboards"/>
<div class="levels-container">
    {#await getLevels()}
        <p>Fetching levels ...</p>
        <div class="filler-black"></div>
    {:then data}
        {#each data as level (level)}
            <Level levelName={level.level_name} levelPoints={level.level_points} levelRank={level.level_rank} />
        {/each}
    {:catch error}
        <p>{error.message}</p>
    {/await}

</div>