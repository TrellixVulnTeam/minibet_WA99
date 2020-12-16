<style>

.tabs-wrap {
    min-height: 3rem;
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 0rem 1.5rem 0rem 1.5rem;
    white-space: nowrap;
    overflow: auto;
}

.tabs-active {
    background-color: #ddd;
    margin-right: 0.5rem;
    min-width: 3rem;
    min-height: 3rem;
    text-align: center;
    padding: 0rem 2rem 0rem 2rem;
    border-radius: 1.5rem 1.5rem 1.5rem 0;
    font-weight: bold;
    color: #111;
    cursor: pointer;
}

.tabs-inactive {
    background-color: #111;
    margin-right: 0.5rem;
    min-width: 3rem;
    min-height: 3rem;
    text-align: center;
    padding: 0rem 2rem 0rem 2rem;
    border-radius: 1.5rem 1.5rem 1.5rem 0;
    font-weight: bold;
    color: #AAA;
    cursor: pointer;
}

</style>

<template>

<div class="tabs-wrap" style="margin-top: 3rem">
  <div v-for="tab in tabs" :key="tab.id" :class="{'tabs-active': tab.isActive, 'tabs-inactive': !tab.isActive}" :style="tab.style" class="flex-dead-center" @click="tabClicked(tab)">{{tab.label}}</div>
</div>

</template>

<script>

export default {
    name: 'Tabs',
    data() { // variable declarations
        return {
          tabs: [
            {id: 0, label: 'For Me', isActive: true},
            {id: 1, label: 'Matches', isActive: false},
            {id: 2, label: 'Trending Games', isActive: false, style:[{'min-width':'110px'}]},
            {id: 3, label: 'Top Rated', isActive: false, style:[{'min-width':'80px'}]}
          ]
        }
    },
    methods:{
      tabClicked(object){
        this.$emit('tabClickedEvent',object)// passing the whole object onto the parent vue where the component is loaded
      }
    }
}

</script>
