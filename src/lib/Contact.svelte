<script> 
import axios from "axios"
let name = ""
let lastname = ""
let email = ""
let message = ""

function handleOnSubmit(event){
    event.preventDefault()
    axios.post("http://localhost:8056/items/Contact", {
        name,
        lastname ,
        email ,
        message 
    })
    .then(function(resp){

    })
    .catch(function(error){
        
    })
}
</script>

<section id="contact">
    <h1>Formulaire de Contact</h1>
<form class="contact" on:submit={handleOnSubmit}>

    
    

    <div class="field_infos">
        <label for="name">NOM</label>
            <input class="input_infos" type="text" id="name" placeholder="Linda" bind:value={name}>
    </div>
    <div class="field_infos">
        <label for = "lastname">PRENOM</label>
            <input class="input_infos" type="text" id="lastname" placeholder="Wal" bind:value={lastname} >
    </div>
    <div class="field_infos">
        <label for="email">EMAIL</label>
            <input class="input_infos" type="email" id="email" placeholder="linda@boite.com" bind:value={email}>
    </div>
    <div class="field_infos" >
        <label for="message">MESSAGE </label>
            <input class="input_infos" type="message" id="message" placeholder="****" bind:value={message}>
    </div>
    
    <div class="field_infos">
       
        <button class="send">Envoyer</button>
    </div>
    </form>
</section>
    <style></style>

