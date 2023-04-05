<!-- On importe le menu pour le header -->
<script>
    import Menu from "./menu.svelte";
    import bandeau from "../assets/Banniere header V1.jpg"
    
</script>

<!-- On place l'image pour le bandeau du header -->
<header>
     <Menu/>
    <div aria-hidden="true" class="bandeau">
        <img src="{bandeau}" alt="bannière header"> 
    </div>
</header>

<style>
img {

    max-width:50rem ;
    display: flex;
    
    position: absolute;
    top: 35%;
    left: 50%;
    transform: translate(-50%, -50%);

}


</style>