<script>
  import axios from "axios";
  import { push } from "svelte-spa-router";
  import Button from "../composants/Button.svelte";

  let articles = [];

  // Récupère la liste des articles
  axios
    .get("http://localhost:8056/items/Article?fields=*.*")
    .then(function (resp) {
      articles = resp.data.data;
    })
    .catch(function (error) {});

  // Fonction pour naviguer vers la page de l'article sélectionné
  function afficherArticle(id) {
    push(`/article/${id}`);
  }

</script>

<Button/>


{#each articles as article}
  <article>
    <!-- Utilise un bouton pour rendre le titre interactif et accessible -->
    <button on:click={() => afficherArticle(article.articleId)}>
      <h2>{article.title}</h2>
    </button>
    
    <p>{article.content.slice(0, 100)}...</p>
  </article>
{/each}


<style>
  article {
  border: 1px solid #ddd;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  padding: 40px;
  margin-bottom: 40px;
}

button {
background: none;
border: none;
padding: 0;
cursor: pointer;
text-align: left;
}

button h2 {
font-size: 36px;
font-weight: bold;
margin-bottom: 20px;
}
/* h2 {
  font-size: 36px;
  font-weight: bold;
  margin-bottom: 20px;
} */

p {
  font-size: 18px;
  line-height: 1.6;
  margin-bottom: 30px;
}

article:hover {
  transform: translateY(-5px);
  box-shadow: 0px 7px 14px rgba(0, 0, 0, 0.2);
  transition: transform 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
}

</style>

