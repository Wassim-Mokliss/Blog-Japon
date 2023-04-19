<script>
    //J'importe mon outil de travail
    import axios from "axios";
    
    //Je parametre le refresh sur non
    //export let reload = false;

    //J'importe une fonctionnalité
    import {push} from "svelte-spa-router";

    const isRegistered = window.localStorage.getItem('token') != null;
    if ( isRegistered ) {
        window.localStorage.removeItem('token');
        location.reload();
    }

    //Je defini mes variables d'environnement qui vont transporter les infos du clients
    let last_name=""
    let first_name=""
    let email=""
    let password=""

    //Je parametre les erreur des champs en booleen sur non
    let error_boolean = false;

   function handleOnSubmit(event) {
        event.preventDefault()
        const registerData = JSON.stringify({last_name, first_name, email, password});
        const registerOptions = {
            headers: {
                'Content-Type': 'application/json',
            }
        }
        axios.post("http://localhost:8056/users", registerData, registerOptions)

        .then(function(res) {
            // Inscription réussi, maintenant la connexion
            console.log("Inscription réussi ...")
            const loginData = JSON.stringify({email, password});
            const loginOptions = {
                headers: {
                    'Content-Type': 'application/json',
                }
            };

            axios.post("http://localhost:8056/auth/login", loginData, loginOptions)
            .then(function(res) {
                // Connexion réussie, on récupère le token et redirection vers la page d'accueil
                console.log("et connexion réussi également !")
                const token = res.data.access_token;
                window.localStorage.setItem('token', token);
                push('/');
            })
            .catch(function(error) {
                console.log("Erreur: mais connexion échouer :(")
                console.log(error);
            });
        })
        .catch(function(error) {
            console.log("Erreur: Inscription échouer :(");
            console.log(error);
        });
    }

    //Fonction qui me permet de verifier si l'adresse email est saisi et si elle est valide
    function validateMessageEmail(event) {
        let textbox = event.target;
        error_boolean = false;
        if (textbox.value === '') {
                textbox.setCustomValidity('Champ requis');
            } else if (textbox.validity.typeMismatch){
                error_boolean = true;
                textbox.setCustomValidity('Veuillez inserer une adresse email valide.');
            } else {
            textbox.setCustomValidity('');
            }
            return true;
    }
</script>

<div class="logister">

    <div class="allform">

        <form   on:submit={handleOnSubmit}
                on:invalid={validateMessageEmail}
                on:changed={validateMessageEmail}
                on:input={validateMessageEmail}>

        <h2 class="title_register">Inscription</h2>

                <div class="infos">
                    <label class="title_field_register" for="lastname">Nom :</label>
                    <input class="input_register" required type="lastname" name="lastname" id="lastname" placeholder="Doe" bind:value={last_name}/>
                </div>

                <div class="infos">
                    <label class="title_field_register" for="firstname">Prénom :</label>
                    <input class="input_register" required type="firstname" name="firstname" id="firstname" placeholder="John" bind:value={first_name}/>
                </div>

                <div class="infos">
                    <label class="title_field_register" for="email">Email :</label>
                    <input class="input_register" required type="email" name="email" id="email" placeholder="johndoe@email.com" bind:value={email}/>
                    {#if error_boolean}
                        <h1 class="error_msg">Adresse email invalide</h1>
                    {/if}
                    <a href="/#/connexion">Déjà inscrit ?</a>
                </div>

                <div class="infos">
                    <label class="title_field_register" for="password">Mot de passe :</label>
                    <input class="input_register" required type="password" name="password" id="password" placeholder="**********" bind:value={password}/>
                </div>

                <div class="divsubmitbtn">
                    <button class="btnsubmit" type="submit">Crée un compte</button>
                </div>

        </form>
    
    </div>

</div>

<style lang="scss">

    a {
        margin-left: 130px;
        font-size: 13px;
        text-decoration: none;
        color: #0077cc;

            &:hover {
                text-decoration: underline;
                color: #004f88;
            }
        
    }

</style>