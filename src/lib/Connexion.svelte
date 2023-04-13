<script>
//   import axios from 'axios';
//   import { push } from 'svelte-spa-router';

//   // Création des variables liées aux champs de formulaire
//   let email = '';
//   let password = '';

//   // Fonction asynchrone pour gérer la soumission du formulaire
//   async function handleLogin(event) {
//     event.preventDefault();
//     try {
//       // Envoi d'une requête POST à l'API directus/auth/login avec les données du formulaire
//       const response = await axios.post('http://localhost:8056/auth/login', { email, password });

//       // Si la requête réussit et renvoie un objet success:true
//       if (response.data.success) {
//         // Redirection de l'utilisateur vers la page d'acceuil
//         push('/acceuil');
//       } else {
//         // Redirection de l'utilisateur vers la page d'inscription
//         push('/register');
//       }
//     } catch (error) {
//       // Affichage de l'erreur dans la console en cas d'échec de la requête
//       console.error(error);
//       alert('pas bon')
//     }
//   }

//   console.log(email,password)

import { push } from "svelte-spa-router";

    export let reload = false;

    let email;
    let password;

    const isLogged = window.localStorage.getItem('token') != null;
    if ( isLogged ) {
        window.localStorage.removeItem('token');
        location.reload();
    }

    const handleSubmitForm = async (event) => {
        event.preventDefault();
        const token = await login();
        window.localStorage.setItem('token', token);

        if ( reload ) {
            location.reload();
        }
        else {
            // Naviguer vers la page d'accueil grace à svelte-spa-router
            push('/');
        }
    }

    const login = async () => {
        const endpoint = import.meta.env.VITE_URL_DIRECTUS + "/auth/login";

        const response = await fetch(endpoint, {
            method: "POST",
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({
                "email": email,
                "password": password
            })
        });

        // Extraction du contenu du body de la réponse au format json
        const json = await response.json();

        // Lit uniquement le token du json
        const token = json.data.access_token
        return token;
    }

  

    
    


</script>


<h1>Connexion</h1>



<form on:submit={handleSubmitForm} id="connexion-form" action="" method="post">
    <label for="email">Nom d'utilisateur :</label>
    <input type="email" id="email" bind:value={email}>

    <label for="password">Mot de passe :</label>
    <input type="password" id="password" bind:value={password}>

    <button type="submit">Se connecter</button>
  </form>

  <style>

    form{
        align-items: center;
        text-align: center;
        display: flex;
        flex-direction: column;

    }




  </style>