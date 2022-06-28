<template>
    <div>
        <v-text-field
            v-model="firstName"
            label="first name"
            @keyup="processNameInput"
        />
        <v-text-field
            v-model="lastName"
            label="last name" 
            @keyup="processNameInput"
        />
        <div class="py-4">
            Entered name is: {{ fullName }}
            <v-progress-linear
                v-if="isLoading"
                indeterminate
            />
        </div>
    </div>
</template>

<script>
  export default {
    name: 'AsynchrounousFunction',

    data () {
        return {
            firstName: null,
            lastName: null,
            timer: null,
            fullName: '',
            isLoading: false,
        }
    },

    methods: {
        processNameInput() {
            this.isLoading = true
            clearTimeout(this.timer)
            this.timer = setTimeout(this.displayName, 1000)
        },
        displayName () {
            if (this.firstName.length && this.lastName.length) {
                this.fullName = this.firstName + ' ' + this.lastName
                this.isLoading = false
            }
        }
    }
  }
</script>