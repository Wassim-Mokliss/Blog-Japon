<script>
    import axios from "axios";
    import { push } from "svelte-spa-router";
  
    export let params = {};
    let article = {};
  
    const api = axios.create({
      baseURL: "http://localhost:8056",
    });
  
    async function getImage(imageUuid) {
      try {
        const response = await api.get("/files/" + imageUuid);
        return response.data.data;
      } catch (error) {
        console.error("Error fetching image data:", error);
      }
    }
  
    api
      .get("/items/Article/" + params.id + "?fields=*,image")
      .then(async function (resp) {
        article = resp.data.data;
        if (article.image) {
          article.image = await getImage(article.image);
        }
        console.log(article);
      })
      .catch(function (error) {
        console.error("Error fetching article data:", error);
      });
  
    // Fonction pour retourner à la page Articles.svelte
    function retournerArticles() {
      push(`/articles`);
    }
  
  </script>
  
  <article>
    <button on:click={retournerArticles}>Retourner à la liste des articles</button>
    <h2>{article.title}</h2>
  
    {#if article.image && article.image.filename_disk}
      <img src="http://localhost:8056/assets/{article.image.filename_disk}" alt="Image à la une" class="article-image"/>
    {/if}
  
    <p>{article.content}</p>
    {#if article.label}
        <span class="tag"> {article.label.join(", ")}</span>
    {/if}
  </article>
  
  <style>
    article {
      border: 1px solid #ddd;
      box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
      padding: 40px;
      margin: 40px auto 40px;
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
  
    .article-image {
      max-width: 100%;
      height: auto;
    }
  
    button {
      background: none;
      border: none;
      padding: 0;
      cursor: pointer;
      text-align: left;
      margin-bottom: 20px;
    }
  
    button:hover {
      text-decoration: underline;
    }

    .tag {
        display: inline-block;
        background-color: rgb(253, 222, 222);
        color: #333;
        font-size: 12px;
        font-weight: bold;
        padding: 5px 10px;
        border-radius: 20px;
        margin-top: 10px;
    }
  
  </style>
  