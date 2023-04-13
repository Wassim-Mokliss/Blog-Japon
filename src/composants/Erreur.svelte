<!-- Erreur.svelte -->
<script>
    import { onMount } from 'svelte';
  
    onMount(() => {
      document.title = '404 - Page introuvable';
    });
  </script>
  
  <style>
    .erreur404{
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      text-align: center;
    }
  
    h1 {
      font-size: 6rem;
      margin-bottom: 1rem;
    }
  
    p {
      font-size: 1.5rem;
      margin-bottom: 2rem;
    }
  
    a {
      font-size: 1.2rem;
      text-decoration: none;
      color: #0077cc;
    }
  
    a:hover {
      text-decoration: underline;
    }
  </style>
  
  <div class="erreur404">
    <h1>404</h1>
    <p>La page que vous recherchez est introuvable.</p>
    <a href="/">Retour à la page d'accueil</a>
  </div>