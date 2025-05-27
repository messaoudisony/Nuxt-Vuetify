<template>
    <v-container>
        <v-img :src="image1" max-width="400" class="mx-auto mt-6" />

        <CardSection />
        <FeatureGrid />
    </v-container>
        <Footer/>
</template>

<script setup lang="ts">
import image1 from '~/assets/image1.png'
</script>
