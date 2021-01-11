<style scoped>

.transactionCarousel-wrap {
    display: flex;
    flex-direction: column;
}

.transactionCarousel-content-wrap {
    display: flex;
    flex-direction: row;
    align-items: stretch;
    justify-content: left;
    overflow: scroll;
    padding: 0rem 1.5rem;
}

@media only screen and (min-width: 800px) {
    .transactionCarousel-content-wrap {
        flex-wrap: wrap;
    }
}

</style>

<template>

<div class="transactionCarousel-wrap" style="margin-top: 2rem">
    <segment_heading @seeMoreClickedEvent="addMoreTransactions" :prop_titleStatus="transactionHeading.isExceeded" :prop_caller="transactionHeading.caller" :prop_heading="`${transactionHeading.heading} (${transactionItems.length})`" :prop_cta="transactionHeading.cta" />
    <div class="transactionCarousel-content-wrap" style="margin-top: 1rem">
        <transaction_item v-for="(item, index) in transactionItems" :key="index" :prop_transactionItems="item" />
    </div>
</div>
</template>

<script>

import segment_heading from './common/segment_heading.vue'
import transaction_item from './TransactionCarousel/item.vue'
export default {
    name: 'TransactionCarousel',
    data() { // variable declarations
        return {
            transactionHeading: {
                heading: "Ongoing Transactions",
                cta: "See More",
                caller: this.$options.name, // returns app name
                isExceeded: false
            },
            transactionItems: [],
            transactionProperties : {
              currency : ["RMB","USD","VND","KRW","PHP"],
              status : ["accepted","processing","pending","failed"],
              type : ["deposit","withdrawal","transfer"]
            }
        }
    },
    components: {
        transaction_item,
        segment_heading
    },
    methods: {
        addMoreTransactions() {
          var subject = this.transactionProperties
            if (this.transactionItems.length<16) {
                this.transactionItems.push({
                    id: this.transactionItems.length,
                    currency: subject.currency[this.randomize(subject.currency.length)],
                    value: this.randomize(100000000)/100,
                    dateStamp: this.randomize(59),
                    status: subject.status[this.randomize(subject.status.length)],
                    type: subject.type[this.randomize(subject.type.length)]
                })
                //console.log(`Array length: ${this.transactionItems.length}`)
            }
            else{
              this.transactionHeading.isExceeded = true,
              console.log("No more transactions to display!")
            }
        },
        randomize(limit){
          return Math.floor(Math.random()*limit)
        }
    },
    mounted() {
        //console.log(this.$options.name)

        //console.table(this.transactionItems)
        //this.transactionProperties.currency.forEach( (value, index) => console.log(`${index} ${value}`) )
        //console.log(Object.keys(this.transactionItems[0]))
    },
    created(){
      var i = 0;
      for (i = 0; i < this.randomize(16)+1; i++) {
        this.addMoreTransactions()
      }
    }
}

</script>
