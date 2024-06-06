<script>
    import { dndzone } from 'svelte-dnd-action';
    import Pocketbase from "pocketbase";
    import { onMount } from 'svelte';
    import { flip } from 'svelte/animate';
    const pb = new Pocketbase("http://127.0.0.1:8090");

    async function getPlayers() {
        const records = await pb.collection("level_ranks_and_points").getFullList();
        return records;
    }

    const handleConsider = (evt) => {
        items = evt.detail.items;
    }

    const handleFinalize = (evt) => {
        items = evt.detail.items;
    }

    let items = [];
    onMount(async () => {
        try {
            items = await getPlayers();
        } catch (error) {
            console.error("Error fetching data", error);
        }
    })

</script>

<style>
    .demon {
        display: flex;
        justify-content: space-between;
        gap: 1vw;
        width: 40vw;
    }
    .demons-container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
</style>

<section class="demons-container" 
    use:dndzone="{{items: items}}"
    on:consider="{handleConsider}"
    on:finalize="{handleFinalize}"
    >
    {#each items as item, index (item.id)}
        <div class="demon" animate:flip="{{duration: 250}}">
            <h2>#{index + 1}</h2>
            <h2>{item.level_name}</h2>
        </div>
    {/each}
</section>
