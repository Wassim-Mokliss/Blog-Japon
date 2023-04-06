<script>
  
  import Actuality from "../composants/Actuality.svelte";
  import Banner from "../composants/Banner.svelte";
</script>



<div aria-hidden="true" class="bandeau">
    <img src="./src/assets/banniere.jpg" alt="bannière header">    
</div>

<style lang="scss">
    img { 
   height: 500px;
   background-size: contain;
   width: 100%;
    } 
</style>
<!-- <Banner/> -->
<Actuality/>
