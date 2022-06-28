<template>
    <div>
        <v-btn
            class="mb-4  mt-3"
            @click="fetchUsers"
        >
            Fetch users
        </v-btn>
        <v-btn
            class="mb-4 ml-4  mt-3"
            @click="fetchUsersIncorrectly"
        >
            Try to fetch users
        </v-btn>
        <v-card>
            <v-card-text>
                <v-progress-circular
                    v-if="isLoading"
                    indeterminate
                />
                <v-alert
                    v-if="hasError" 
                    type="error"
                >
                    {{ errorMessage }}
                </v-alert>
                <p v-if="users.length === 0">No users loaded yet</p>
                <ul v-else>
                    <li
                        v-for="user in users"
                        :key="user.id"
                    >
                        {{ user.name }}
                    </li>
                </ul>
            </v-card-text>
        </v-card>
    </div>
</template>

<script>
import axios from 'axios'

  export default {
    name: 'AxiosData',

    data () {
        return {
            users: [],
            isLoading: false,
            hasError: false,
            errorMessage: null,
        }
    },

    methods: {
        async fetchUsers () {
            this.isLoading = true
            this.hasError = false

            await new Promise(r => setTimeout(r, 2000));

            axios.get('https://jsonplaceholder.typicode.com/users')
                .then(resp => {
                    this.users = resp.data
                })
                .catch(error => {
                    this.hasError = true
                    this.errorMessage = error.message
                })
                .finally(() => {
                    this.isLoading = false
                })
        },

        async fetchUsersIncorrectly () {
            this.isLoading = true
            this.hasError = false

            await new Promise(r => setTimeout(r, 2000));

            axios.get('https://jsonplaceholder.typicode.com/users-something')
                .then(resp => {
                    this.users = resp.data
                })
                .catch(error => {
                    this.hasError = true
                    this.errorMessage = error.message
                })
                .finally(() => {
                    this.isLoading = false
                })
        }
    }
  }
</script>