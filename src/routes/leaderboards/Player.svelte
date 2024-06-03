<script lang="ts">
    import Playerdemons from "./Playerdemons.svelte";

    export let playerName: string;
    export let playerPoints: string;
    export let playerRank: number;

    async function getPlayerDemons(playerName: string) {
        return fetch(`https://gdph-demons.pockethost.io/api/player_demons/${playerName}`)
        .then(response => response.json());
    }

    let showPlayerDemons = false;
    let playerBorderStyle = "none";
    function handleDemonClick() {
        showPlayerDemons = !showPlayerDemons;
        if (playerBorderStyle === "none") {
            playerBorderStyle = "solid";
        } else {
            playerBorderStyle = "none";
        }
    }
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');
    * {
        font-family: 'Outfit', sans-serif;
    }
    .player-container {
        width: 60vw;
        border: 2px solid white;
        transition: all 0.5s ease-in-out;
    }
    .player-top-half {
        display: flex;
        width: inherit;
        opacity: 0.8;
        border-radius: 0.7rem;
    }
    .player-rank, .player-information, .player-buttons {
        width: 33vw;
        text-align: center;
        justify-content: center;
        align-content: center;
    }
    .player-buttons > button {
        background-color: transparent;
        color: white;
        border-top: 0px;
        border-left: 0px;
        border-right: 0px;
        border-bottom: 2px solid white;
    }

    h2, h3 {
        color: #fff;
    }

    button {
        font-size: 1.1rem;
    }

</style>

<div class="player-container" style="border-style: {playerBorderStyle}">
    <div class="player-top-half">
        <div class="player-rank">
            <h2>#{playerRank}</h2>
        </div>
        <div class="player-information">
            <h2>{playerName}</h2>
            <h3>{Number(playerPoints).toFixed(2)} Points</h3>
        </div>
        <div class="player-buttons">
            <button on:click={handleDemonClick}>Demons Completed</button>
        </div>
    </div>
    {#if showPlayerDemons}
        <Playerdemons demonData={getPlayerDemons(playerName)}/>
    {/if}
</div>
