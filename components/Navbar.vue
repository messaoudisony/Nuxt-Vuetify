<template>
    <v-app-bar app color="primary" dark flat>
        
        <v-toolbar-title class="text-h5 font-weight-bold text-white">
            MonExo
        </v-toolbar-title>

        <v-btn to="/" variant="text" class="mx-1" color="white" prepend-icon="mdi-home">Accueil</v-btn>
        <v-btn to="/tableau" variant="text" class="mx-1" color="white" prepend-icon="mdi-table">Tableau</v-btn>
        <v-btn to="/contact" variant="text" class="mx-1" color="white" prepend-icon="mdi-email">Contactez-nous</v-btn>
        
        <v-spacer />
        
        <v-switch v-model="isDark" inset hide-details color="pink" :label="`Mode ${isDark ? 'Sombre' : 'Clair'}`"
            class="ml-4" />
    </v-app-bar>
</template>

<script setup>
import { ref, watch } from 'vue'
import { useTheme } from 'vuetify'

const theme = useTheme()
const isDark = ref(theme.global.name.value === 'dark')

watch(isDark, (val) => {
    theme.global.name.value = val ? 'dark' : 'light'
})
</script>
