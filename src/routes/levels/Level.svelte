<script lang="ts">
    import { fade } from 'svelte/transition';
    import LevelLeaderboard from "./LevelLeaderboard.svelte";

    export let levelName;
    export let levelPoints;
    export let levelRank;

    let showLevelLeaderboards = false;
    let levelBorderStyle = "none";
    
    async function getLevelLeaderboard(levelName: string) {
        return fetch(`https://gdph-demons.pockethost.io/api/level_leaderboard/${levelName}`)
        .then(response => response.json());
    }

</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');
    * {
        font-family: 'Outfit';
    }

    h3, p {
        color: white;
    }

    .level-container {
        width: 60vw;
        border: 2px solid white;
        opacity: 0.8;
        border-radius: 0.7rem;
        transition: all 0.2s ease-in-out;
    }

    .level-information-container {
        display: flex;          
        justify-content: space-between;
        padding: 20px;
    }

    .level-buttons {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: right;
    }

    .level-information {
        width: 20vw;
    }
    .level-buttons > button {
        background: none;
        border: 2px solid white;
        color: white;
        font-size: 1.1rem;
        padding: 0.8rem;
        transition: all 0.25s ease-in-out;
    }
    .level-buttons > button:hover {
        color: black;
        border: 2px solid #ccc;
        box-shadow: inset 8em 0 0 0 white;
    }
    .level-buttons > button:active {
        transform: translateY(5px);
    }
</style>

<div class="level-container" style="border-style: {levelBorderStyle}" transition:fade|global="{{duration: 300, delay: 0}}">
    <div class="level-information-container">
        <div class=level-information>
            <h3>#{levelRank} - {levelName}</h3>
            <p>{levelPoints} Points</p>
        </div>
        <div class="level-buttons">
            <button class="leaderboards-btn" on:click={() => {
                showLevelLeaderboards = !showLevelLeaderboards
                if (levelBorderStyle == "none") {
                    levelBorderStyle = "solid";
                } else {
                    levelBorderStyle = "none";
                }
            }}>Leaderboards</button>
        </div>
    </div>
    {#if showLevelLeaderboards}
        <LevelLeaderboard levelLeaderboard={getLevelLeaderboard(levelName)} />
    {/if}
</div>
