<button on:click={redirectToUrl}>{text}</button>

<script>
  //Definir les propriétés du bouton et definir l'url vers laquelle rediriger
  export let text = 'Creer article';
  export let url = '../#/create-article';
  // Apres avoir defini l'evenement "click" dans le code HTML, appeler une fonction de gestion d'événement qui effectue la redirection en utilisant la méthode "window.location.href"
  function redirectToUrl() {
    window.location.href = url;
  }
</script>
<style>
  button {
    background-color: #fc2e2e;
    color: rgb(255, 255, 255);
    font-size: 20px;
    padding: 8px 16px;
    border: none;
    border-radius: 4px;
    }

    button:hover{
        background-color: #ffb6c1;
        color: #fc2e2e;
    }

</style>