<script>
    import { writable } from "svelte/store";
    let currentMenu = "leaderboards";
    export const store = writable("leaderboards")
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');
* {
    font-family: 'Outfit';
}
.menu-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: black;
    width: 100vw;
}

.buttons {
    display: flex;
    gap: 2vw;
    padding-right: 2rem;
}

p {
    text-decoration: none;
    color: white;
}

.logo-name-name {
    padding-left: 2rem;
}

.logo-name-name > h2 {
    color: white;
}

</style>

<div class="menu-container">
    <div class="logo-name-name">
        <h2>GDPH Demonlist</h2>
    </div>

    <div class="buttons">
        <a href="/"><p>Home</p></a>
        <a href="/levels"><p>Top 150 List</p></a>
        <a href="/leaderboards"><p>Leaderboards</p></a>
        <a href="/"><p>Changelogs</p></a>
        <a href="/"><p>Guidelines</p></a>
        <a href="/"><p>About Us</p></a>
    </div>
</div>