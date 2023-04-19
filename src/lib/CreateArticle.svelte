 <!-- Importation de la bibliothèque axios pour effectuer des requêtes HTTP  -->
<script>
    import axios from "axios";
  
    // Déclaration des variables pour stocker les valeurs des champs du formulaire
    let formData = {
        title: "",
        label: "",
        content: "",
        image: null
    }

    function submitArticle(event){
      event.preventDefault ()
      const token = window.localStorage.getItem('token');
      const data = JSON.stringify(formData);
          const options = {
              headers: {
                  'Content-Type': 'application/json',
                  'Authorization': `Bearer ${token}`
              }
            }
      // Envoie une requête POST à l'API de Directus avec les données du formulaire
      axios.post("http://localhost:8056/items/Article", data, options)
      
        // Traite la réponse en cas de succès
        .then(function (response) {
          console.log("Article créé avec succès", response.data);
        })
        // Traite l'erreur en cas d'échec
        .catch(function (error) {
          console.error("Erreur lors de la création de l'article", error);
        });
    }
  </script>


<!-- Début du formulaire avec la classe "submitArticle" et la fonction "submitArticle" appelée lors de la soumission du formulaire -->

<form class="submitArticle" on:submit={submitArticle}>
  
  <div class="infos_article">
    <label for="title">Titre:</label>
    <input type="text" id="title" name="title" bind:value={formData.title}/>
  </div>

    <div class="infos_article">
        <label for="label-tag">Label</label>
        <select name="label-tag" id="label-tag" bind:value={formData.label}>
          <option value="">Choisir une catégorie...</option>
          <option value='["Jeux vidéos"]'>Jeux vidéos</option>
          <option value='["Mangas"]'>Mangas</option>
          <option value='["Événements"]'>Événements</option>
        </select>
    </div>

    <div class="infos_articles">
        <label for="content">Description:</label>
        <input id="content" name="content" bind:value={formData.content}/>
    </div>

    <div class="infos_article_btn">
        <!-- Bouton pour soumettre le formulaire -->
        <button type="submit">Créer un article</button>
    </div>

</form>
  
  <style>
    /* Applique un style à la classe "submitArticle", définissant la disposition des éléments, l'espacement, la largeur maximale et la police */
.submitArticle {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 600px;
  margin: 0 auto;
  font-family: Arial, sans-serif;
}

/* Applique un style au label à l'intérieur de la classe "submitArticle", définissant la taille et la graisse de la police */
.submitArticle label {
  font-size: 1.2rem;
  font-weight: bold;
}

/* Applique un style aux champs input et textarea à l'intérieur de la classe "submitArticle", définissant la marge intérieure, la taille de la police, la bordure et le rayon de la bordure */
.submitArticle input, .submitArticle textarea {
  padding: 0.5rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

/* Applique un style au bouton à l'intérieur de la classe "submitArticle", définissant la couleur d'arrière-plan, la couleur du texte, la marge intérieure, la taille de la police, la bordure, le rayon de la bordure et le curseur */
.submitArticle button {
  background-color: #e72727;
  color: white;
  padding: 1rem;
  font-size: 1.2rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

/* Applique un style au bouton lorsqu'il est survolé, modifiant la couleur d'arrière-plan pour un effet de surbrillance */
.submitArticle button:hover {
  background-color: #a04545;
}

  </style>