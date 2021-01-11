<style lang="scss" scoped>
.item-wrap{

  display: flex;
  flex-direction: column;
  min-width: 9rem;
  min-height: 11rem;
  border-radius: 0.75rem 0.75rem 0.75rem 0;
  margin-right: 0.5rem;
  background-color: #fff;
  transition: min-width 0.8s, border-radius 0.2s, background-color 0.2s;
  transition-timing-function: ease-in;
  cursor: pointer;

  &:hover{
    border-radius: 0.75rem 0 0.75rem 0.75rem;
    background-color: #ddd;
    transition: border-radius 0.2s, background-color 0.2s;
  }

  .thumbnail{
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

  .value{
    margin-left: 0.5rem;
    color: #111;
    font-size: 1rem;
  }

  .dateStamp{
    margin-left: 0.5rem;
    color: #11111160;
    font-size: 0.75rem;
  }

  .status{
    margin: 1rem 1rem 0 0;
    text-align: right;
    text-transform: uppercase;
    color: #11111180;
    font-size: 0.75rem;
  }

}

.item-wrap

.thumbnail-deposit{
  background-image: url("../../assets/icons/outline/branded/deposit.png");
}

.thumbnail-withdrawal{
  background-image: url("../../assets/icons/outline/branded/withdrawal.png");
}

.thumbnail-transfer{
  background-image: url("../../assets/icons/outline/branded/transfer.png");
}
/*:style="{ backgroundImage: 'url(' + transactionIcons[0].url + ')' }"
:class="{'bgTomato': carouselItem.type=='deposit', 'bgAqua': carouselItem.type=='withdrawal'}"
style="background-image: url('../../assets/icons/outline/branded/deposit.png')"
*/

@media only screen and (min-width: 800px) {
  .item-wrap{
    min-height: 0;
    margin-top: 0.5rem;
    min-width: 48.8%;
    transition: min-width 0.8s, border-radius 0.2s, background-color 0.2s;
    transition-timing-function: ease-in;
    flex-direction: row;
    align-items: center;
  }

  .item-wrap .thumbnail{
    width: 2.5rem;
    height: 2.5rem;
    background-size: 1.75rem;
  }

  .item-wrap .status{
    flex-grow: 2;
    margin-top: 0;
  }

}
</style>
<template>
  <div class="item-wrap" @click="redirectURL()">
    <div class="thumbnail" :class="getItemThumbnail()"></div>
    <div class="value">{{`${getSign()} ${prop_transactionItems.currency} ${calc_transactionItems.value}`}}</div>
    <div class="dateStamp">{{`${prop_transactionItems.dateStamp} mins ago`}}</div>
    <div class="status" :class="{'txtTomato': prop_transactionItems.status=='failed','txtOrange': prop_transactionItems.status=='pending'}">{{prop_transactionItems.status}}</div>
  </div>
</template>
<script>
export default {
    name: 'item',
    data() { // variable declarations
        return {
          calc_transactionItems : {value: Intl.NumberFormat().format(this.prop_transactionItems.value)}
        }
    },
    props:{
      prop_transactionItems: Object
    },
    methods:{
      getItemThumbnail(){
        return {
          'thumbnail-deposit': this.prop_transactionItems.type=='deposit',
          'thumbnail-withdrawal': this.prop_transactionItems.type=='withdrawal',
          'thumbnail-transfer': this.prop_transactionItems.type=='transfer'
        }
      },
      redirectURL(){
        var subject = this.prop_transactionItems
        //console.log("i'm passing an " + this.prop_transactionItems.constructor.name),
        //console.table(this.prop_transactionItems),
        this.$router.push({ name: 'Detail', params: { prop_txnValue: subject.value, prop_txnCurrency: subject.currency, prop_txnDateStamp: subject.dateStamp, prop_txnStatus: subject.status, prop_txnType: subject.type, prop_txnId: subject.id }})
        //alert("clicked");
        //window.location.href = 'Detail.vue';
      },
      getSign(){
        return this.prop_transactionItems.type=='deposit' ? '+'
        : this.prop_transactionItems.type=='withdrawal' ? '-' : '>'
      }
    }
}

</script>
