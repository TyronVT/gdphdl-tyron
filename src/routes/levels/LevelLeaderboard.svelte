<script>
    import { fade, slide } from 'svelte/transition';
    export let levelLeaderboard;
</script>

<style>
    .level-leaderboard {
        display: flex;
        justify-content: space-around;
        text-align: left;
        flex-direction: column;
        padding: 1rem;
    }
    .separator {
        border-top: 3px solid #bbbb;
    }
    p {
        color: white;
    }
</style>

<div class="level-leaderboard">
    <div class="separator" transition:slide|global="{{duration: 500, delay: 0}}"></div>
    {#await levelLeaderboard}
        <p transition:slide|global="{{duration: 300, delay: 0}}">Fetching level leaderboard...</p>
    {:then data}
        {#if data.length < 1}
            <p transition:slide|global="{{duration: 300}}">This demon remains undefeated.</p>
        {:else}
            {#each data as player, index (player)}
                <p transition:slide|global="{{duration: 300, delay: index*100}}">{index + 1}. {player.player_name}</p>
            {/each}
        {/if}
    {:catch error}
        <p>error.message</p>
    {/await}
</div>