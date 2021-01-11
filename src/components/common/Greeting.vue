<style scoped>

.greeting-wrap {
    display: flex;
    flex-direction: row;
    align-items: left;
    padding: 0rem 1.5rem;
}

.greeting-wrap div.content {
    color: #eee;
    display: flex;
    flex-direction: column;
    text-align: left;
    margin-left: 0.5rem;
}

.greeting-wrap div.content div:nth-child(1) {
    font-size: 1.125rem;
    letter-spacing: -0.01875rem;
}

.greeting-wrap div.content div:nth-child(2) {
    font-size: 1.5rem;
    letter-spacing: -0.0375rem;
}

.greeting-icon{
  height: 3.25rem;
  width: 3.25rem;
  background-image: url("../../assets/icons/outline/greeting/morning.png");
  background-size: contain;
  background-repeat: no-repeat;
}
@media only screen and (min-width: 600px) {
    .greeting-wrap div.content {
        flex-direction: row;
    }

    .greeting-wrap div.content div:nth-child(2) {
        font-size: 1.125rem;
        margin-left: 0.5rem;
    }

    .greeting-icon{
      height: 1.625rem;
      width: 1.625rem;
      background-image: url("../../assets/icons/outline/greeting/morning-sm.png");
      background-size: contain;
    }
}

</style>

<template>

<div class="greeting-wrap" style="margin-top: 1.25rem">
    <div class="greeting-icon"></div>
    <div class="content">
        <div>{{greetings[getTimeOfDay()]}}</div>
        <div>Enzo</div>
    </div>
</div>

</template>

<script>

export default {
    name: 'Greeting',
    data() { // variable declarations
        return {
            greetings: ["Good Morning", "Good Afternoon", "Good Evening"]
        }
    },
    methods: {
        getTimeOfDay() {
            var currentDate = new Date();
            var currentHour = currentDate.getHours();
            var timeOfDay = 0;

            switch (true) {
                case currentHour >= 0 && currentHour <= 11:
                    timeOfDay = 0;
                    break;
                case currentHour >= 12 && currentHour <= 17:
                    timeOfDay = 1;
                    break;
                case currentHour >= 18 && currentHour <= 23:
                    timeOfDay = 2;
                    break;
                default:
                    break;
            }

            return timeOfDay;
        }
    },
    mounted() {

    }
}

</script>
