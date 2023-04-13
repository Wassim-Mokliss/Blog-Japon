<script>
      import Router from "svelte-spa-router";
      import Home from "./lib/Home.svelte";
      import Articles from "./lib/Articles.svelte";
      import Connexion from "./lib/Connexion.svelte"
      import A_propos from "./lib/A_propos.svelte"
      

      const routes = {
      '/': Home,
      '/articles': Articles,
      '/login': Connexion,
      '/a-propos' : A_propos,
      }
</script>

     
     

<Header/>
<main>
  <Router {routes}/>
</main>
<Footer/>

