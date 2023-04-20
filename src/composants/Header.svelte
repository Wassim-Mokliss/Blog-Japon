<script>
    import {link} from 'svelte-spa-router';
    import logo from '../assets/LogoJapnco.png';

    const isLogged = window.localStorage.getItem('token') != null;

    const nav_links = [
        {   
            text: "Accueil", 
            url: "/",
            label: "Page principal"
        },
        {   
            text: "Articles",
            url: "/articles",
            label: "Page affichant tout les articles publiés"
        },
        {   
            text: isLogged ? "Se déconnecter" : "Se connecter",
            url: "/connexion",
            label: "Page affichant le formulaire de connexion et qui donne la possibilité d'être rediriger vers le formulaire d'inscription si besoin"
        }
];



</script>

<header>
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
</header>

<style lang="scss">




.liens_menu {
        font-size: 24px;
        margin: 0 15px;
    }

    .logo_img {
        width: 75px;
        height: 75px;
    }
    
    .logo_title {
        font-size: 35px;
        margin-top: -30px;
        margin-bottom: 25px;
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