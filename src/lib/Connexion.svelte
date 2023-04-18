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

<div class="logister">

    <div class="allform">   

        <form on:submit={handleSubmitForm} action="" method="post">

            <h2 class="title_login">Connexion</h2>
                
                <div class="infos">
                    <label for="email">Email :</label>
                    <input class="input_login" type="email" id="email" placeholder="john@doe.com" bind:value={email}>
                    <a href="/#/inscription">Pas encore inscrit ?</a>
                </div>

                <div class="infos">          
                    <label for="password">Mot de passe :</label>
                    <input class="input_login" type="password" id="password" placeholder="**********" bind:value={password}>
                </div>
            
                <div class="divsubmitbtn">
                    <button class="btnsubmit" type="submit">Se connecter</button>
                </div>

        </form>

    </div>

</div>

<style lang="scss">

    a {
        margin-left: 100px;
        font-size: 13px;
        text-decoration: none;
        color: #0077cc;

            &:hover {
                text-decoration: underline;
                color: #004f88;
            }
        
    }

</style>