<script>
    import {link} from 'svelte-spa-router';
    import logo from '../assets/LogoJapnco.png';

    const nav_links = [
       { text: "Accueil", url: "/", label: ""},
       { text: "Articles", url: "/articles", label: "" },
       { text: "Connexion/Inscription", url: "/connexion", label: "" }
];



</script>


<nav class="navheader" aria-label="menu principal">
    
    <a use:link href="/" title="Jap&CO" aria-label="accueil du site">
        <img class="logo_img" src="{logo}" alt="Logo"> 
    </a>

    <h1 class="logo_title">Jap&Co</h1>

    <ul id="menu" role="menu" aria-labelledby="toggle-menu">
        <!-- Utilisation d'une boucle pour créer la navigation dynamiquement -->
        {#each nav_links as nav}
            <li role="none">
                <a class="liens_menu" use:link href="{nav.url}" role="menuitem" aria-label="{nav.label}">{nav.text}</a>
            </li>
        {/each}
    </ul>

    
    <button class="searchbtn" type="button" id="toggle-menu" aria-controls="menu" aria-haspopup="true">
        <i id="menubutton" class="fa-solid fa-bars"></i>
    </button>
    <form class="formsearch" action="/search" method="GET">
        <input type="text" name="q" placeholder="Rechercher" class="searchinput">
        <input type="image" src="./src/assets/loupe.png" value="Rechercher" class="submitloupe" aria-label="loupe">
      </form>
</nav>

<style lang="scss">

    .liens_menu {
        font-size: 28px;
        margin: 0 15px;
    }

    .logo_img {
        width: 150px;
        height: 150px;
    }
    
    .logo_title {
        font-size: 70px;
        margin-top: -60px;
        margin-bottom: 50px;
    }

    .formsearch {
        display: flex;
        justify-content: space-evenly;
    }

    .submitloupe {
        width: 35px;
        height: 35px;
    }

    .searchinput {
        background-color: rgba(255, 255, 255, 0.9);
        border-radius: 7px;
        padding: 0 15px;
        margin-right: 15px;
        width: 20vw;
        font-style: italic;
    }

    .searchinput::placeholder {
        color: rgba(0, 0, 0, 0.7);
        text-align: center;
        font-size: 16px;
    }

   
</style>


