

<script>
    import axios from "axios"
  import BtnArticle from "../composants/BtnArticle.svelte";
    let articles = [
    
    ]
    //axios.get("http://localhost:8056/items/Article/1c6e944a-1894-4712-98fb-1d0233dd9b4b") => récupère un article en particulier par son ID
    axios.get("http://localhost:8056/items/Article")
    .then(function(resp){
        articles = resp.data.data
    })
    .catch(function(error){
        
    })
</script>


{#each articles as article}
<article>
    <h2>{article.title}</h2>
    <p>{article.label}</p>
    <p>{article.content}</p>
</article>
{/each}
<style></style>