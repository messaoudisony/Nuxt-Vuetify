<template>
    <v-card class="pa-4" rounded="xl" elevation="1">
        <v-row align="center" no-gutters>
            <v-avatar size="48" class="mr-4" :style="{ backgroundColor: bgColor }">
                <v-icon size="28" color="white">{{ icon }}</v-icon>
            </v-avatar>
            <div>
                <h3 class="text-subtitle-1 font-weight-bold">{{ title }}</h3>
                <p class="text-body-2">{{ description }}</p>
            </div>
        </v-row>
    </v-card>
</template>

<script setup>
defineProps({
    title: String,
    description: String,
    icon: String,
    bgColor: String
})
</script>
