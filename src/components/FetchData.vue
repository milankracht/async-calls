<template>
    <div>
        <v-btn
            class="mb-4 mt-3"
            @click="fetchTasks"
        >
            Fetch data
        </v-btn>
        <v-card>
            <v-card-text>
                <p v-if="tasks.length === 0">No tasks loaded yet</p>
                <ul v-else>
                    <li
                        v-for="task in tasks"
                        :key="task.id"
                    >
                        {{ task.title }}
                        <v-icon
                            v-if="task.completed"
                            color="green"
                        >
                            mdi-check
                        </v-icon>
                        <v-icon
                            v-else
                            color="red"
                        >
                            mdi-close
                        </v-icon>
                    </li>
                </ul>
            </v-card-text>
        </v-card>
    </div>
</template>

<script>
  export default {
    name: 'FetchData',

    data () {
        return {
            tasks: []
        }
    },

    methods: {
        fetchTasks () {
            fetch('https://jsonplaceholder.typicode.com/todos')
                .then(response => response.json())
                .then(json => {
                    this.tasks = json
                })
        }
    }
  }
</script>