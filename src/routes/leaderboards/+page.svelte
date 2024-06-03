<script lang="ts">
    import Player from "./Player.svelte";
    import Titlepage from "../Titlepage.svelte";
    import Pocketbase from "pocketbase";

    const pb = new Pocketbase("https://gdph-demons.pockethost.io");

    async function getPlayers() {
        const records = await pb.collection("player_ranks_and_points").getFullList();
        return records;
    }
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');

    * {
        font-family: 'Outfit';
    }

    :global(body) {
        margin: 0;
        padding: 0;
        overflow-x: hidden;
    }

    .leaderboards-container{
        display: flex;
        flex-direction: column;
        background-color: black;
        align-items: center;
        gap: 1.5vw;
    }

</style>

<Titlepage titleName="Leaderboards" description="Players of the GDPH Demon List" />
<div class="leaderboards-container">
    {#await getPlayers()}
        <p> Fetching players ... </p>
    {:then data}
        {#each data as player, index}
            <Player playerName={player.player_name} playerRank={index + 1} playerPoints={player.total_points} />
        {/each}
    {:catch error}
        <p>{error.message}</p>
    {/await}
</div>