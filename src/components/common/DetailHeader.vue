<style scoped>

/* logo */

.header-wrap {
    min-height: 4rem;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding: 0rem 1.5rem 0rem 1.5rem;
}

.label-wrap {
    display: flex;
    justify-content: left;
    padding-left: 1rem;
    font-size: 1.125rem;
    color: #eee;
    text-transform: capitalize;
}

.ico_back {
    min-width: 1.5rem;
    min-height: 1.5rem;
    background-image: url("../../assets/icons/outline/arrow_back.png");
    background-size: contain;
    cursor: pointer;
}

.ico_more {
    min-width: 1.5rem;
    min-height: 1.5rem;
    background-image: url("../../assets/icons/outline/more.png");
    background-size: contain;
}

@media only screen and (min-width: 600px) {

}

</style>

  <template>

  <div class="header-wrap">
      <div class="ico_back" @click="backToHome"></div>
      <div class="label-wrap" style="flex-grow: 2">
          {{ transactionType }} Transaction
      </div>
      <div class="ico_more"></div>
  </div>


  </template>

<script>

export default {
    name: 'MinibetHeader',
    data() { // variable declarations
        return {
          burgerToggleStatus: false
        }
    },
    computed: {
      transactionType : function(){
        return this.prop_transactionType
      }
    },
    methods:{
      backToHome(){
        this.$router.push("/Home")
      }
    },
    props:{
      prop_transactionType: String
    }
}

</script>
