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

.logo-wrap {
    display: flex;
    justify-content: center;
}

.logo-wrap div {
    width: 4.375rem;
    height: 1.5rem;
    background-image: url("../../assets/logo-hi-res.png");
    background-size: cover;
}

.ico_burger {
    min-width: 1.5rem;
    min-height: 1.5rem;
    background-image: url("../../assets/icons/outline/burger.png");
    background-size: contain;
}

.ico_notification {
    min-width: 1.5rem;
    min-height: 1.5rem;
    background-image: url("../../assets/icons/outline/bell.png");
    background-size: contain;
}

@media only screen and (min-width: 600px) {
  .logo-wrap{
    justify-content: left;
    padding-left: 1.5rem;
  }

}

</style>

  <template>

  <div class="header-wrap">
      <div class="ico_burger" @click="burgerToggle"></div>
      <div class="logo-wrap" style="flex-grow: 2">
          <div></div><!-- logo container -->
      </div>
      <div class="ico_notification"></div>
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
    methods:{
      burgerToggle(){
        this.burgerToggleStatus = !this.burgerToggleStatus,
        console.log(this.burgerToggleStatus)
      }
    }
}

</script>
