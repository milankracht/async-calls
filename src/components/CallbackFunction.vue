<template>
    <div>
        <v-text-field v-model="firstName" label="first name" />
        <v-text-field v-model="lastName" label="last name" />
        <v-btn @click="processNameInput(displayFullName)">Process</v-btn>
        <div id="demo" class="py-4"></div>
    </div>
</template>

<script>
  export default {
    name: 'CallbackFunction',

    data () {
        return {
            firstName: null,
            lastName: null,
        }
    },

    methods: {
        displayFullName(string) {
            document.getElementById('demo').innerHTML = string
        },

        processNameInput(myCallback) {
            let fullName = 'Entered name is: ' + this.firstName + ' ' + this.lastName
            myCallback(fullName)
        },
    }
  }
</script>