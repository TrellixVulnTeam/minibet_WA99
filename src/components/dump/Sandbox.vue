<style scoped>

#app {
    font-family: Times New Roman;
}

</style>

<template>

<p>

    {{ `${msg}: ${fullName}, ${followers}` }}</p>
<p @click="incrementFollowers" style="cursor: pointer">increment</p>

</template>

<script>

export default {
    name: 'Sandbox',
    data() { // variable declarations
        return {
            followers: 0,
            user: {
                firstName: this.initFirstName,
                lastName: this.initLastName
            }
        }
    },
    watch: { // listener for changes in variables
      followers(newFollowerCount,oldFollowerCount){
        console.log(`${oldFollowerCount} ${newFollowerCount}`)
      }
    },
    props: { // dependency variables
        msg: String,
        initFirstName: String,
        initLastName: String,
        initFollowers: Number
    },
    computed: { // calculated variables - variables should be assigned a function that returns something
        fullName() {
            return `${this.user.firstName} ${this.user.lastName}`
        }
    },
    methods: { // functions
        incrementFollowers() {
            this.followers += parseInt(this.initFollowers)
        }
    },
    mounted() { //onLoad event
        this.incrementFollowers()
    }
}

</script>
