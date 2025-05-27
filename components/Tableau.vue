<template>
    <div>
        <v-card class="mb-4 pa-4 mt-4" theme="dark">
            <v-row>
                <v-col cols="12" md="2">
                    <v-select v-model="itemsPerPage" :items="itemsPerPageOptions" label="Affichage" />
                </v-col>

                <v-col cols="12" md="3">
                    <v-select v-model="sortField" :items="sortOptions" label="Trier par" item-title="text"
                        item-value="value" />
                </v-col>

                <v-col cols="12" md="3">
                    <v-select v-model="sortOrder" :items="orderOptions" label="Ordre" item-title="text"
                        item-value="value" />
                </v-col>
            </v-row>
        </v-card>

        <v-table theme="dark">
            <thead>
                <tr>
                    <th scope="col" class="text-left">FirstName</th>
                    <th scope="col" class="text-left">LastName</th>
                    <th scope="col" class="text-left">Age</th>
                    <th scope="col" class="text-left">Gender</th>
                    <th scope="col" class="text-left">Email</th>
                    <th scope="col" class="text-left">Address</th>
                    <th scope="col" class="text-left">EyeColor</th>
                    <th scope="col" class="text-left">BloodGroup</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user in paginatedData" :key="user.id">
                    <td>{{ user.firstName }}</td>
                    <td>{{ user.lastName }}</td>
                    <td>{{ user.age }}</td>
                    <td>{{ user.gender }}</td>
                    <td>{{ user.email }}</td>
                    <td>{{ user.address.city }}</td>
                    <td>{{ user.eyeColor }}</td>
                    <td>{{ user.bloodGroup }}</td>
                </tr>
            </tbody>
        </v-table>

        <div class="text-center mt-4">
            <v-pagination v-model="currentPage" :length="totalPages" :total-visible="7" />
        </div>
    </div>

    <div>
        <v-row justify="center" class="align-center">
            <v-col cols="auto">
                <span class="text-caption">Version 1.2</span>
            </v-col>

            <v-divider vertical class="mx-4" />

        
            <v-col cols="auto">
                <span class="text-caption">Works via Chrome</span>
            </v-col>
        </v-row>
    </div>
</template>


<script setup>
import { ref, computed, watch } from 'vue'


const { data } = await useFetch('https://dummyjson.com/users')
const originalUsers = data.value.users

const currentPage = ref(1)
const itemsPerPage = ref(10)
const sortField = ref('')
const sortOrder = ref('asc')

const itemsPerPageOptions = [5, 10, 15, 20]
const sortOptions = [
    { text: 'Aucun tri', value: '' },
    { text: 'FirstName', value: 'firstName' },
    { text: 'Age', value: 'age' }
]
const orderOptions = [
    { text: 'Ordre croissant', value: 'asc' },
    { text: 'Ordre décroissant', value: 'desc' }
]

const sortedUsers = computed(() => {
    if (!sortField.value) return [...originalUsers]

    return [...originalUsers].sort((a, b) => {
        let aValue = a[sortField.value]
        let bValue = b[sortField.value]

        if (typeof aValue === 'string') aValue = aValue.toLowerCase()
        if (typeof bValue === 'string') bValue = bValue.toLowerCase()

        const comparison = aValue > bValue ? 1 : aValue < bValue ? -1 : 0
        return sortOrder.value === 'desc' ? -comparison : comparison
    })
})

const totalPages = computed(() => Math.ceil(sortedUsers.value.length / itemsPerPage.value))

const paginatedData = computed(() => {
    const start = (currentPage.value - 1) * itemsPerPage.value
    return sortedUsers.value.slice(start, start + itemsPerPage.value)
})


watch([sortField, sortOrder, itemsPerPage], () => {
    currentPage.value = 1
})

</script>
