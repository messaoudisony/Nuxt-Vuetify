<template>
    <v-container>
        <h1>Formulaire de Contact</h1>
        <v-form @submit.prevent="envoyer">
            <v-text-field label="Nom" v-model="nom" required />
            <v-text-field label="Email" v-model="email" type="email" required />
            <v-textarea label="Message" v-model="message" required />

            <v-btn type="submit" color="primary" class="mt-2">Envoyer</v-btn>
        </v-form>
    </v-container>
</template>

<script setup>
const nom = ref('')
const email = ref('')
const message = ref('')

const envoyer = () => {
    alert(`Message envoyé par ${nom.value} (${email.value})`)
}
</script>
