<template>
    <div class="py-12 text-center">
        <v-chip color="green-lighten-3" class="mb-4 text-green-darken-2">Subheading</v-chip>
        <h2 class="text-h5 font-weight-bold mb-2">Build your website with Blank</h2>
        <p class="text-body-1 mb-10">
            No matter what project you're working on, we've got you covered with the best wireframe kits for any
            platform.
        </p>

        <v-container>
            <v-row dense>
                <v-col cols="12" md="6" lg="6">
                    <FeatureCard title="Design system"
                        description="The shortest way to create a cool design starts here. Fully customizable and neatly organized components."
                        icon="mdi-palette" bg-color="#ec4899" />
                </v-col>
                <v-col cols="12" md="6" lg="6">
                    <FeatureCard title="Components"
                        description="Fully customizable and neatly organized components will help you work faster without limiting creative freedom."
                        icon="mdi-puzzle" bg-color="#8b5cf6" />
                </v-col>
                <v-col cols="12" md="6" lg="6">
                    <FeatureCard title="Auto layout"
                        description="Neatly organized components with auto layout to save you time and help create structure."
                        icon="mdi-view-grid-plus" bg-color="#22c55e" />
                </v-col>
                <v-col cols="12" md="6" lg="6">
                    <FeatureCard title="Lifetime updates"
                        description="Free updates forever. Stay up to date with the latest components and improvements."
                        icon="mdi-star-four-points" bg-color="#a855f7" />
                </v-col>
            </v-row>
        </v-container>
    </div>
</template>

<script setup>
import FeatureCard from './FeatureCard.vue'
</script>
