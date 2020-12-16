<!--template> // Sandbox template
  <img style="width: 70px; height: 24px;" alt="Vue logo" srcset="./assets/logo-hi-res.png">
  <Sandbox msg="First component instance" initFollowers="10" initFirstName="Anthony" initLastName="Pena"/>
  <Sandbox msg="Second component instance" initFollowers="20" initFirstName="Melanie" initLastName="Lagman"/>
</template-->

<template>
  <MinibetHeader />
  <Greeting />
  <Tabs @tabClickedEvent="selectPage"/>
  <TransactionCarousel />
</template>

<script>
//import Sandbox from './components/Sandbox.vue'
import MinibetHeader from './components/MinibetHeader.vue'
import Greeting from './components/Greeting.vue'
import Tabs from './components/Tabs.vue'
import TransactionCarousel from './components/TransactionCarousel.vue'

export default {
  name: 'App',
  components: {
    MinibetHeader,
    Greeting,
    Tabs,
    TransactionCarousel
    //Sandbox
  },
  methods:{
    selectPage(object){
      console.log(object)
    }
  }
}
</script>

<style>
#app {
  font-family: Source Sans Pro;
}

body {
  background-color: #333;
  margin: 0rem auto;
  min-width: 20rem;
  max-width: 50rem;
}
</style>
