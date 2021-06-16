<template>
    <!-- Header section -->
    <header>
        <h1>
            <img
                src="https://www.wildcodeschool.com/assets/logo_main-e4f3f744c8e717f1b7df3858dce55a86c63d4766d5d9a7f454250145f097c2fe.png"
                alt="Wild Code School logo"
            />
            Les Argonautes
        </h1>
    </header>

    <!-- Main section -->
    <main>
        <!-- New member form -->
        <h2>Ajouter un(e) Argonaute</h2>
        <form class="new-member-form">
            <label for="name">Nom de l&apos;Argonaute</label>
            <input
                id="name"
                name="name"
                type="text"
                placeholder="Charalampos"
            />
            <button type="submit">Envoyer</button>
        </form>
		<!-- Member list -->
        <h2>Membres de l'équipage</h2>
        <section class="member-list">
            <div class="member-item">Eleftheria</div>
            <div class="member-item">Gennadios</div>
            <div class="member-item">Lysimachos</div>
        </section>
        
    </main>

    <footer>
        <p>Réalisé par Jason en Anthestérion de l'an 515 avant JC</p>
    </footer>
</template>

<script setup lang="ts">

</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto&display=swap");

body {
    margin: 0;
    font-family: "Roboto", sans-serif;
    background-color: white;
    color: black;
}

main {
    max-width: 960px;
    margin: 0 auto;
}

header {
    background: #f4f4f4;
    text-align: center;
    padding: 2em;
}

header img {
    max-width: 96px;
}

header h1 {
    font-size: 2.5em;
}

h1,
h2 {
    text-align: center;
}

label {
    display: block;
    margin-bottom: 0.5em;
}

.new-member-form {
    margin: 2em 0 4em 0;
    text-align: center;
}

.member-item {
    padding: 0.25em 0;
}

footer {
    margin-top: 2em;
    text-align: center;
    color: #fff;
    background: #f76c6c;
    padding: 0.25em 0;
}
</style>
