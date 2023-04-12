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

<form on:submit={handleOnSubmit}>

    <h1>Formulaire de Contact</h1>
    

    <div class="field">
        <label for="name">NOM</label>
            <input type="text" id="name" placeholder="Linda" bind:value={name}>
    </div>
    <div class="field">
        <label for = "lastname">PRENOM</label>
            <input type="text" id="lastname" placeholder="Wal" bind:value={lastname} >
    </div>
    <div class="field">
        <label for="email">EMAIL</label>
            <input type="email" id="email" placeholder="linda@boite.com" bind:value={email}>
    </div>
    <div class="field" >
        <label for="message">MESSAGE </label>
            <input type="message" id="message" placeholder="****" bind:value={message}>
    </div>
    
    <div class="field">
        <input type="submit" class="send" value="Me connecter">
    </div>
    </form>

    <style></style>

