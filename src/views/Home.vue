<template>
  <MinibetHeader />
  <Greeting />
  <Tabs @tabClickedEvent="selectPage"/>
  <TransactionCarousel />
  <MatchCarousel />
</template>

<script>
//import Sandbox from './components/Sandbox.vue'
import MinibetHeader from './../components/common/MinibetHeader.vue'
import Greeting from './../components/common/Greeting.vue'
import Tabs from './../components/common/Tabs.vue'
import TransactionCarousel from './../components/TransactionCarousel.vue'
import MatchCarousel from './../components/MatchCarousel.vue'

export default {
  name: 'Home',
  components: {
    MinibetHeader,
    Greeting,
    Tabs,
    TransactionCarousel,
    MatchCarousel
    //Sandbox
  },
  methods:{
    selectPage(object,name,age){
      console.log(object.label + " " + name + " " + age)
    }
  },
  mounted(){

  }
}
</script>
