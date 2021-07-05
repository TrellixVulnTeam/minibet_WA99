<!--template> // Sandbox template
  <img style="width: 70px; height: 24px;" alt="Vue logo" srcset="./assets/logo-hi-res.png">
  <Sandbox msg="First component instance" initFollowers="10" initFirstName="Anthony" initLastName="Pena"/>
  <Sandbox msg="Second component instance" initFollowers="20" initFirstName="Melanie" initLastName="Lagman"/>
</template-->

<!--
<style></style>
<template></template>
<script></script>
-->

<template>
  <router-view />
</template>

<script>
//import Sandbox from './components/Sandbox.vue'
//import Home from './views/Home.vue'

export default {
  name: 'App',
  components: {
    //Home
    //Sandbox
  },
  methods:{},
  mounted(){}
}
</script>

<style lang="scss">
//see common.scss

</style>
