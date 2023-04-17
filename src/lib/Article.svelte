

<script>
    import axios from "axios"
    export let params = {};
    let article = {

    }
    
     //=> récupère un article en particulier par son ID
    axios.get("http://localhost:8056/items/Article/"+params.id)
    .then(function(resp){
        article = resp.data.data
   
    })
    .catch(function(error){
        
    })
</script>

<article>
    <h2> {article.title}</h2>
    <p>{article.description}</p>n
</article>
<style></style>


  