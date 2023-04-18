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
    <p>{article.content}</p>
</article>
<style>
    article {
    border: 1px solid #ddd;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    padding: 40px;
    margin: 40px auto 40px ;
    width: 600px;
    
}

h2 {
    font-size: 36px;
    font-weight: bold;
    margin-bottom: 20px;
} 

p {
    font-size: 18px;
    line-height: 1.6;
    margin-bottom: 30px;
}


</style>

  