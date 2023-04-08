<script>
      import Router from "svelte-spa-router";
      import Home from "./lib/Home.svelte";
      import Articles from "./lib/Articles.svelte";
      import Header from "./composants/Header.svelte";
      import Footer from "./composants/Footer.svelte";
      


      const routes = {
      '/': Home,
      '/articles': Articles,
      }
</script>

     
     

<Header/>
<main>
  <Router {routes}/>
</main>
<Footer/>

