<script>
    export let form;
    import Titlepage from "../Titlepage.svelte";
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');

    * {
        font-family: 'Outfit';
        color: white;
    }
    :global(body) {
        margin: 0;
        padding: 0;
        overflow-x: hidden;
    }
    .content-container {
        display: flex;
        justify-content: center;
        width: 100vw;
        height: 100vh;
        background-color: black;
    }
    button {
        background-color: black;
        border: 2px solid white; 
    }
    input {
        width: 100%;
        background-color: black;
        border: none;
        border-bottom: 2px solid white;
        font-size: 1vw;
        padding: 10px;
    }
    input:focus {
        border: 3px solid red;
    }
    button {
        font-size: 1vw;
    }
</style>

<Titlepage titleName="Admin Login" description= ""/> 
<div class="content-container">
    <form method="POST" action="?/login">
        <label>
            Email
            <input name="email" type="email">
        </label>
        
        <br>    

        <label>
            Password
            <input name="password" type="password">
        </label>
        
        <br><br>
        
        <button type="submit">Log In</button>
    
    </form>
</div>