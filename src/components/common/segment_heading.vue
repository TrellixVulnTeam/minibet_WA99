<style>

.heading-wrap{
  min-height: 1.5rem;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  padding: 0rem 1.5rem;
}

.heading-wrap .title{
  font-size: 1.125rem;
  color: #eeeeee80;
  letter-spacing: -0.01875rem;
}

.heading-wrap .titleError{
  color: tomato;
}

.heading-wrap .more{
  font-size: 1rem;
  color: #eee;
  cursor: pointer;
  transition: transform 0.2s, color 0.4s;
}

.heading-wrap .moreDisabled{
  cursor: default;
  color: #444;
}

.heading-wrap .more:hover{
  transform: scale(1.1);
  transition: transform 0.2s, color 0.4s;
  color: #ff8800;
}

</style>
<template>

  <div class="heading-wrap">
    <div class="title" :class="{'titleError':this.prop_titleStatus}">{{this.prop_heading}}</div>
    <div :class="{'moreDisabled':this.prop_titleStatus, 'more':!this.prop_titleStatus}" @click="seeMore(this.prop_caller)">{{this.prop_cta}}</div>
  </div>

</template>
<script>
export default {
    name: 'segment_heading',
    data() { // variable declarations
        return{}
      },
      props:{
        prop_heading: String,
        prop_cta: String,
        prop_caller: String,
        prop_titleStatus: Boolean
      },
      methods:{
        seeMore(caller){
          //console.log(caller.constructor.name)
          this.$emit('seeMoreClickedEvent',caller)
        }
      }
    }
</script>
