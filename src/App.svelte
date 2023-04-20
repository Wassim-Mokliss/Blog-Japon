<script>
      import Router from "svelte-spa-router";
      import Home from "./lib/Home.svelte";
      import Articles from "./lib/Articles.svelte";
      import Article from "./lib/Article.svelte";
      import Contact from "./lib/Contact.svelte";      
      import Header from "./composants/Header.svelte";
      import Footer from "./composants/Footer.svelte";
      import Connexion from "./lib/Connexion.svelte";
      import A_propos from "./lib/A_propos.svelte";
      import Erreur from "./composants/Erreur.svelte";
      import CreateArticle from "./lib/CreateArticle.svelte";
      import Register from "./lib/Register.svelte";

      const routes = {
      '/': Home,
      '/articles': Articles,
      '/article/:id': Article,
      '/create-article': CreateArticle,
      '/connexion' : Connexion,
      '/inscription': Register,
      '/contact' : Contact,
      
      '/a-propos' : A_propos,
      '*': Erreur

      }
      
      //Test

</script>

     
     

<Header/>
<main>
  <Router {routes}/>
</main>
<Footer/>

<style lang="scss">

  /*main {
    flex: 1,
  }*/

</style>