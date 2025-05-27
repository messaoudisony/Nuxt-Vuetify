<template>
    <v-table  theme="dark">
        <thead>
            <tr>
                <th class="text-left">FirstName</th>
                <th class="text-left">LastName</th>
                <th class="text-left">Age</th>
                <th class="text-left">Gender</th>
                <th class="text-left">Email</th>
                <th class="text-left">Adress</th>
                <th class="text-left">EyeColor</th>
                <th class="text-left">BloodGroup</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="item in paginatedData" :key="item.id">
                <td>{{ item.firstName }}</td>
                <td>{{ item.lastName }}</td>
                <td>{{ item.age}}</td>
                <td>{{ item.gender }}</td>
                <td>{{ item.email }}</td>
                <td>{{ item.address.city }}</td>
                <td>{{ item.eyeColor }}</td>
                <td>{{ item.bloodGroup }}</td>
            </tr>
        </tbody>
    </v-table>
    <div class="text-center mt-4">
            <v-pagination
                v-model="currentPage"
                :length="totalPages"
                :total-visible="7"
            ></v-pagination>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue'


const currentPage = ref(1)
const itemsPerPage = 10

const totalPages = computed(() => Math.ceil(users.length / itemsPerPage))


const paginatedData = computed(() => {
    const start = (currentPage.value - 1) * itemsPerPage
    const end = start + itemsPerPage
    return users.slice(start, end)
})
const { data } = await useFetch('https://dummyjson.com/users')
const users = data.value.users
</script>