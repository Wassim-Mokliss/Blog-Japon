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

    header{
display: flexbox;
align-content: flex-start;
width: 100%;


    }

    /* .bandeau {

height: 300px;
background-image: url("../assets/Banniere\ header\ V1.jpg");
background-size: cover;
background-position: center;

} */
 img {

    
    display: flex;
    position: absolute;
    top: 30%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-size: cover;
    height: 290px;
    /* min-width: 100%; */
    

} 


</style>