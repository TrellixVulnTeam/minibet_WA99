<style scoped>

.matchCarousel-wrap {
    display: flex;
    flex-direction: column;

}

.matchCarousel-content-wrap {
    display: flex;
    flex-direction: row;
    align-items: stretch;
    justify-content: left;
    overflow: scroll;
    padding: 0rem 1.5rem;
}

@media only screen and (min-width: 800px) {}

</style>

<template>

<div class="matchCarousel-wrap" style="margin-top: 2rem">
    <segment_heading @seeMoreClickedEvent="addMoreMatches" :prop_titleStatus="matchHeading.isExceeded" :prop_caller="matchHeading.caller" :prop_heading="`${matchHeading.heading} (${matchItems.length})`" :prop_cta="matchHeading.cta" />
    <div class="matchCarousel-content-wrap" style="margin-top: 1rem">
        <match_item v-for="(item, index) in matchItems" :key="index" :prop_MatchItems="item" />
    </div>
</div>

</template>

<script>

import segment_heading from './common/segment_heading.vue'
import match_item from './MatchCarousel/item.vue'
export default {
    name: 'MatchCarousel',
    data() { // variable declarations
        return {
            matchHeading: {
                heading: "Favoured Matches",
                cta: "See More",
                caller: this.$options.name, // returns app name
                isExceeded: false
            },
            matchItems: [],
            matchProperties : {
              teams : ["Arsenal","Bolton","Chelsea","Liverpool","Wigan Warriors","Tottenham Hotspurs","Manchester City","Ginebra United"],
              status : ["up","down"]
            }
        }
    },
    components: {
        match_item,
        segment_heading
    },
    methods: {
        addMoreMatches() {
            var subject = this.matchProperties
            if(this.matchItems.length<20){
            this.matchItems.unshift({
                id: this.matchItems.length,
                betTypeCount: this.randomize(50),
                teamA: subject.teams[this.getRivalIndex()[0]],
                teamB: subject.teams[this.getRivalIndex()[1]],
                status: subject.status[this.randomize(subject.status.length)]
            })
          }
          else{
            this.matchHeading.isExceeded = true,
            console.log("Match number exceeded!")
          }
        },
        randomize(limit){
          return Math.floor(Math.random()*limit)
        },
        getRivalIndex(){
          var teamIndex = []
          teamIndex.push(this.randomize(this.matchProperties.teams.length))
          var i
          var x
          for (i = 0; i < this.matchProperties.teams.length; i++) {
            x = this.randomize(this.matchProperties.teams.length)
            if (x!=teamIndex[0]){
              teamIndex.push(x)
              break
            }
            //console.log("x = "+x)
          }
          //console.log(teamIndex)
          return teamIndex
        }
    },
    mounted() { //onLoad event
      var i = 0;
      for (i = 0; i < this.randomize(19)+1; i++) {
        this.addMoreMatches()
      }
      //console.table(this.matchItems)
    }
}

</script>
