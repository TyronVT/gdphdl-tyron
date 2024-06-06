<script>
    let isOpen = false;
    function toggleNav() {
        isOpen = !isOpen;
    }
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');
* {
    font-family: 'Outfit';
}

a {
    text-decoration: none;
}

.menu-container-mobile {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: black;
    width: 100dvw;
    transition: transform 0.3s ease-in-out;
}

.menu-container-mobile.closed {
    transform: translateX(-100%);
}

.menu-container-desktop {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: black;
    width: 100dvw;
    transition: transform 0.3s ease-in-out;
}

.buttons {
    display: flex;
    padding-right: 2vw;
    gap: 1vw;
}

h2 {
    font-size: 1.5vw;
}

a {
    font-size: 1vw;
}

p {
    text-decoration: none;
    color: white;
}

.logo-name-name {
    padding-left: 2vw;
}

.logo-name-name > h2 {
    color: white;
}

#menu-close-button {
    display: none;
}

.hamburger-menu {
    display: none;
}

/* Phones CSS */
@media (max-width: 480px) {
    .hamburger-menu {
        display: flex;
        width: 100dvw;
        background-color: black;
        align-items: center;
        justify-content: space-between;
        overflow-x: hidden;
    }
    
    .hamburger-menu > button {
        color: white;
        background-color: black;
        font-size: 10vw;
        padding-left: 2.5vw;
        padding-right: 2.5vw;
        border: none;
    }

    .hamburger-menu > h1 {
        font-size: 5vw;
        padding-left: 5vw;
    }

    .menu-container-mobile {
        padding-top: 3vh;
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-content: center;
        position: fixed;
        width: 70%;
        height: 100%;
        z-index: 1;
        top: 0;
        left: 0;
        gap: 5vh;
        overflow-x: hidden;
        transform: translateX(-100%);
    }

    .menu-container-mobile.open {
        transform: translateX(0%);
    }

    .menu-container-desktop {
        display: none;
    }

    .buttons {
        display: flex;
        flex-direction: column;
        gap: 10vw;
        align-items: center;
        width: inherit;
    }

    a {
        font-size: 4vw;
    }

    h2 {
        font-size: 6vw;
    }

    h1 {
        color: white;
    }

    .menu-button {
        display: flex;
        justify-content: center;
        width: 50vw;
        background-color: black;
        border: 2px solid #666;
        border-radius: 7px;
    }

    .logo-name-name {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 10vw;
    }

    #menu-close-button {
        display: block;
        font-size: 10vw;
        background-color: black;
        color: white;
        border: none;
    }
}

/* Desktop CSS */
@media (min-width: 481px) {
    .hamburger-menu {
        display: none;
    }

    .menu-container-mobile {
        display: none;
    }

    .menu-container-desktop {
        display: flex;
    }
}
</style>

<div class="hamburger-menu">
    <h1>GDPH Demonlist</h1>
    <button on:click={toggleNav}>≡</button>
</div>

<div class="menu-container-mobile {isOpen ? 'open' : 'closed'}">
    <div class="logo-name-name">
        <h2>GDPH Demonlist</h2>
        <button id="menu-close-button" on:click={toggleNav}>&times;</button>
    </div>

    <div class="buttons">
        <div class="menu-button">
            <a href="/"><p>Home</p></a>
        </div>
        
        <div class="menu-button">
            <a href="/levels"><p>Top 150 List</p></a>
        </div>
        
        <div class="menu-button">
            <a href="/leaderboards"><p>Leaderboards</p></a>
        </div>
        
        <div class="menu-button">
            <a href="/"><p>Changelogs</p></a>
        </div>
        
        <div class="menu-button">
            <a href="/"><p>Guidelines</p></a>
        </div>
        
        <div class="menu-button">
            <a href="/"><p>About Us</p></a>
        </div>

        <div class="menu-button">
            <a href="/login"><p>Sign In</p></a>
        </div>
    </div>
</div>

<div class="menu-container-desktop">
    <div class="logo-name-name">
        <h2>GDPH Demonlist</h2>
    </div>

    <div class="buttons">
        <div class="menu-button">
            <a href="/"><p>Home</p></a>
        </div>
        
        <div class="menu-button">
            <a href="/levels"><p>Top 150 List</p></a>
        </div>
        
        <div class="menu-button">
            <a href="/leaderboards"><p>Leaderboards</p></a>
        </div>
        
        <div class="menu-button">
            <a href="/"><p>Changelogs</p></a>
        </div>
        
        <div class="menu-button">
            <a href="/"><p>Guidelines</p></a>
        </div>
        
        <div class="menu-button">
            <a href="/"><p>About Us</p></a>
        </div>

        <div class="menu-button">
            <a href="/login"><p>Sign In</p></a>
        </div>
    </div>
</div>