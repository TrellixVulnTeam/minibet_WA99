<style>

.carousel-wrap {
    display: flex;
    flex-direction: column;
    white-space: nowrap;
    overflow: auto;
}

.carousel-heading-wrap{
  min-height: 1.5rem;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  padding: 0rem 1.5rem 0rem 1.5rem;
}

.carousel-heading-wrap .title{
  font-size: 1.125rem;
  color: #eeeeee80;
  letter-spacing: -0.01875rem;
}

.carousel-heading-wrap .more{
  font-size: 1rem;
  color: #eee;
}

.carousel-content-wrap{
  min-height: 11rem;
  display: flex;
  flex-direction: row;
  align-items: stretch;
  justify-content: left;
  overflow: scroll;
  padding: 0rem 1.5rem 0rem 1.5rem;
}

</style>

<template>

<div class="carousel-wrap" style="margin-top: 2rem">
    <div class="carousel-heading-wrap">
      <div class="title">Ongoing Transactions</div>
      <div class="more">See more</div>
    </div>
    <div class="carousel-content-wrap" style="margin-top: 1rem">
      <item v-for="item in transactionItems" :key="item.id" :prop_transactionItems="item" />
    </div>
</div>

</template>

<script>
import item from './TransactionCarousel/item.vue'

export default {
    name: 'TransactionCarousel',
    data() { // variable declarations
        return {
          transactionItems:[
            {id: 0, currency: "RMB", value: 20000, dateStamp: "10 mins ago", status: "processing", type: "deposit"},
            {id: 1, currency: "USD", value: 12345, dateStamp: "3 hours ago", status: "pending", type: "withdrawal"},
            {id: 2, currency: "VND", value: 8881234, dateStamp: "1 year ago", status: "accepted", type: "deposit"},
            {id: 3, currency: "RMB", value: 20000, dateStamp: "10 mins ago", status: "processing", type: "deposit"},
            {id: 4, currency: "USD", value: 12345, dateStamp: "3 hours ago", status: "pending", type: "withdrawal"},
            {id: 5, currency: "VND", value: 8881234, dateStamp: "1 year ago", status: "accepted", type: "withdrawal"}
          ]
        }
    },
    components: {
      item
    }
}

</script>
