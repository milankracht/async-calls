<template>
    <v-container>
        <v-row>
            <v-col cols="6" style="min-height: 50vh">
                <v-card>
                    <v-card-text>
                        <h2>Callback function</h2>
                        <CallbackFunction />
                    </v-card-text>
                </v-card>
            </v-col>
            <v-col cols="6">
                <v-card>
                    <v-card-text>
                        <h2>Asynchronous function</h2>
                        <AsynchronousFunction />
                    </v-card-text>
                </v-card>
            </v-col>
            <v-col cols="6">
                <v-card>
                    <v-card-text>
                        <h2>API call (fetch)</h2>
                        <FetchData />
                    </v-card-text>
                </v-card>
            </v-col>
            <v-col cols="6">
                <v-card>
                    <v-card-text>
                        <h2>API call (axios)</h2>
                        <AxiosData />
                    </v-card-text>
                </v-card>
            </v-col>
        </v-row>
  </v-container>
</template>

<script>
    import CallbackFunction from './CallbackFunction.vue'
    import AsynchronousFunction from './AsynchronousFunction.vue'
    import FetchData from './FetchData.vue'
    import AxiosData from './AxiosData.vue'

    export default {
        name: 'MainLayout',
        components: {
            CallbackFunction,
            AsynchronousFunction,
            FetchData,
            AxiosData,
        },

        data () {
            return {
            }
        },

        methods: {
        }
    }
</script>
