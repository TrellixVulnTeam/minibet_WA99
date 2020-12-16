<style>
.item-wrap{
  min-width: 9rem;
  margin-right: 0.5rem;
  border-radius: 0.75rem 0.75rem 0.75rem 0;
  background-color: #fff;
  display: flex;
  flex-direction: column;
}

.item-wrap .thumbnail{
  width: 5rem;
  height: 5rem;
  margin: 0.5rem;
  background-color: #222;
  border-radius: 0.75rem 0.75rem 0 0.75rem;
  /*background-image: url("../../assets/icons/outline/branded/deposit.png");*/
  background-size: 3.5rem;
  background-position: center;
  background-repeat: no-repeat;
}

.item-wrap .value{
  margin-left: 0.5rem;
  color: #111;
  font-size: 1rem;
}

.item-wrap .dateStamp{
  margin-left: 0.5rem;
  color: #11111160;
  font-size: 0.75rem;
}

.item-wrap .status{
  margin-right: 1rem;
  text-align: right;
  text-transform: uppercase;
  color: #11111180;
  font-size: 0.75rem;
}

.thumbnail-deposit{
  background-image: url("../../assets/icons/outline/branded/deposit.png");
}

.thumbnail-withdrawal{
  background-image: url("../../assets/icons/outline/branded/withdrawal.png");
}
/*:style="{ backgroundImage: 'url(' + transactionIcons[0].url + ')' }"
:class="{'bgTomato': carouselItem.type=='deposit', 'bgAqua': carouselItem.type=='withdrawal'}"
style="background-image: url('../../assets/icons/outline/branded/deposit.png')"
*/
</style>
<template>
  <div class="item-wrap">
    <div class="thumbnail" :class="{'thumbnail-deposit': carouselItem.type=='deposit', 'thumbnail-withdrawal': carouselItem.type=='withdrawal'}"></div>
    <div class="value">{{`${carouselItem.currency} ${carouselItem.value}`}}</div>
    <div class="dateStamp">{{carouselItem.dateStamp}}</div>
    <div class="status">{{carouselItem.status}}</div>
  </div>
</template>
<script>
export default {
    name: 'item',
    data() { // variable declarations
        return {
          carouselItem: {
            currency: this.prop_transactionItems.currency,
            value: this.prop_transactionItems.value,
            dateStamp: this.prop_transactionItems.dateStamp,
            status: this.prop_transactionItems.status,
            type: this.prop_transactionItems.type
          }
        }
    },
    props:{
      prop_currency: String,
      prop_transactionItems: Array
    }
}

</script>
