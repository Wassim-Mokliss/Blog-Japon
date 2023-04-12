<script>
      import Router from "svelte-spa-router";
      import Home from "./lib/Home.svelte";
      import Articles from "./lib/Articles.svelte";
      import Contact from "./lib/Contact.svelte";
      import Header from "./composants/Header.svelte";
      import Footer from "./composants/Footer.svelte";
      import Logister from "./lib/Logister.svelte";
      


      const routes = {
      '/': Home,
      '/articles': Articles,
      '/contact' : Contact,
      '/connexion' : Logister
      }
</script>

     
     

<Header/>
<main>
  <Router {routes}/>
</main>
<Footer/>

