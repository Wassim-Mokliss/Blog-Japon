<script>
    import {link} from "svelte-spa-router"
    
    const nav_links = [
       { text: "À propos", url: "/a-propos", label: "" },
       { text: "Contact", url: "/contact", label: "" },
       { text: "Cookies", url: "/a-propos", label: "" },
];

</script>

   <nav class="navfooter"> 
        <ul class="navitem" id="footer" role="menu" aria-labelledby="toggle-menu">
            <!-- Utilisation d'une boucle pour créer la navigation dynamiquement -->
            {#each nav_links as nav}
                <li role="none">
                    <a use:link href="{nav.url}" role="menuitem" aria-label="{nav.label}">{nav.text}</a>
                </li>
            {/each}
        </ul>

        <p class="copyright">All rights reserved - Jap&Co 2023</p>

    </nav>

     
    


<style lang="scss">
    
    .navfooter {
        display: flex;
        align-items: center;
        flex-direction: column;
        justify-content: center;
        background-color: black;
        color: white;
        height: 70px;
        width: auto;
    }

    .navitem {
        text-decoration: underline;
        display: flex;

        li {
        margin-right: 20px;
      
        a {
        color: white;
        text-decoration: none;
        font-size: 18px;
        transition: all 0.3s ease;
        
        &:hover {
          color: #ffb6c1;
          animation: pulse 1s;
        }
      }
    }
    }

    .copyright {
        margin-top: 8px;
        font-size: 12px;
    }

</style>


    
    
