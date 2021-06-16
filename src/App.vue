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
        <form @submit.prevent="addNewArgonaut()" class="new-member-form">
            <label for="name">Nom de l&apos;Argonaute</label>
            <input
                id="name"
                name="name"
                v-model="inputName"
                type="text"
                placeholder="Charalampos"
            />
            <button type="submit">Envoyer</button>
        </form>
        <!-- Member list -->
        <h2>Membres de l'équipage</h2>
		<button class="member-reload" @click="loadArgonauts()">Recharger la liste</button>
        <section v-if="argonautsList.length" class="member-list">
            <div
                class="member-item"
                v-for="{ id, name } in argonautsList"
                :key="id"
            >
                {{ name }}
            </div>
        </section>
        <section v-else>Chargement en cours...</section>
    </main>

    <footer>
        <p>Réalisé par Jason en Anthestérion de l'an 515 avant JC</p>
    </footer>
</template>

<script setup lang="ts">
ref: inputName = "";

ref: argonautsList = [] as Array<{ id: number; name: string }>;

const loadArgonauts = async () => {
    argonautsList = await fetch(
        `${import.meta.env.VITE_API_URL}/argonaut?select=*`,
        {
            headers: {
                apikey: `${import.meta.env.VITE_API_KEY}`,
            },
        }
    ).then((res) => res.json());
};
const addNewArgonaut = async () => {
    await fetch(`${import.meta.env.VITE_API_URL}/argonaut`, {
        method: "POST",
        headers: {
            apikey: `${import.meta.env.VITE_API_KEY}`,
            "Content-Type": "application/json",
        },
        body: JSON.stringify({ name: inputName }),
    });
    inputName = "";
    loadArgonauts();
};

loadArgonauts();
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
	display: flex;
	flex-direction: column;
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

.member-reload {
	margin: 0 auto;
}

.member-list {
	margin: 1.25rem auto 0 auto;
	display: grid;
	grid-template-columns: 1fr 1fr 1fr;
	place-content: center;
	gap: 0.5rem 3rem;
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
