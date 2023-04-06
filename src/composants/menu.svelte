<script>
    import logo from '../assets/LogoJap&.png'
    const nav_links = [

       { text: "Accueil", url: "/", label: "" },
       { text: "Articles", url: "/articles", label: "" },
       { text: "À propos", url: "/a-propos", label: "" },
       { text: "Connexion", url: "/a-propos", label: "" },
       { text: "Contact", url: "/contact", label: "" },
];



</script>


<nav aria-label="menu principal">
    
    <a href="/" title="Jap&CO" aria-label="accueil du site">
        <img src="{logo}" alt="Logo"> 
    </a>

    <h1>Jap&Co</h1>

    <ul id="menu" role="menu" aria-labelledby="toggle-menu">
        <!-- Utilisation d'une boucle pour créer la navigation dynamiquement -->
        {#each nav_links as nav}
            <li role="none">
                <a href="{nav.url}" role="menuitem" aria-label="{nav.label}">{nav.text}</a>
            </li>
        {/each}
    </ul>

    
    <button type="button" id="toggle-menu" aria-controls="menu" aria-haspopup="true">
        <i id="menubutton" class="fa-solid fa-bars"></i>
    </button>
    <form action="/search" method="GET">
        <input type="text" name="q" placeholder="Rechercher...">
        <input type="submit" value="Rechercher">
      </form>
</nav>


