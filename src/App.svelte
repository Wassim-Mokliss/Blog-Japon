<script>
      import Router from "svelte-spa-router";
      import Home from "./lib/Home.svelte";
      import Articles from "./lib/Articles.svelte";

      import Contact from "./lib/Contact.svelte";

      
      import Header from "./composants/Header.svelte";
      import Footer from "./composants/Footer.svelte";
      import Logister from "./lib/Logister.svelte";
      import Connexion from "./lib/Connexion.svelte";
      import A_propos from "./lib/A_propos.svelte";
      import Erreur from "./composants/Erreur.svelte";


      


      const routes = {
      '/': Home,
      '/articles': Articles,
      '/connexion' : Logister,
      '/contact' : Contact,
      '/login': Connexion,
      '/a-propos' : A_propos,
      '*': Erreur,
      }
</script>

     
     

<Header/>
<main>
  <Router {routes}/>
</main>
<Footer/>

