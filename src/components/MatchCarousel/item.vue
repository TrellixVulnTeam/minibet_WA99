<style lang="scss" scoped>

.item-wrap {
    min-width: 6rem;
    min-height: 7rem;
    transition: border-radius 0.2s, background-color 0.2s;
    transition-timing-function: ease-in;
    margin-right: 0.5rem;
    border-radius: 0.75rem 0.75rem 0.75rem 0;
    background-color: #222;
    display: flex;
    flex-direction: column;
    cursor: pointer;
    &:hover {
        border-radius: 0.75rem 0 0.75rem 0.75rem;
        background-color: #111;
    }
    .rowA {
        display: flex;
        flex-direction: row;
        margin: 0.5rem 0 0 0.25rem;
        .arrows {
            display: flex;
            flex-direction: column;
            div {
                width: 1.5rem;
                height: 1.5rem;
            }
            div:nth-child(1) {
                background-image: url("../../assets/icons/outline/chevron_up-inactive.png");
                background-size: contain;
                background-repeat: no-repeat;
            }
            div:nth-child(2) {
                background-image: url("../../assets/icons/outline/chevron_down-inactive.png");
                background-size: contain;
                background-repeat: no-repeat;
            }
        }
        .bet-type {
            width: 3.5rem;
            margin-left: 0.25rem;
            border-radius: 0.75rem 0.75rem 0 0.75rem;
            background-color: tomato;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: #333;
            color: #eee;
            font-size: var(--font-size);
            transition: font-size 0.2s;
            transition-timing-function: ease-in;
        }
    }
    .rowB {
        display: flex;
        flex-direction: column;
        margin: 1rem 0rem 0 0.75rem;
        font-size: 0.75rem;
        color: #eeeeee80;
        div {
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
            max-width: 4.75rem;
        }
    }
}

</style>

<template>

<div class="item-wrap" @mouseover="itemHovered" @mouseout="itemOut">
    <div class="rowA">
        <div class="arrows">
            <div :style="[prop_MatchItems.status=='up' ? {backgroundImage: `url(${upArrowBG})`} : {}]"></div>
            <div :style="[prop_MatchItems.status=='down' ? {backgroundImage: `url(${downArrowBG})`} : {}]"></div>
        </div>
        <div class="bet-type" :style="betTypeStyle">
            <div>{{prop_MatchItems.betTypeCount}}+</div>
        </div>
    </div>
    <div class="rowB">
        <div>{{prop_MatchItems.teamA}}</div>
        <div>{{prop_MatchItems.teamB}}</div>
    </div>
</div>

</template>

<script>

import upArrowURL from "../../assets/icons/outline/chevron_up-active.png";
import downArrowURL from "../../assets/icons/outline/chevron_down-active.png";

export default {
    name: 'item',
    data() { // variable declarations
        return {
            upArrowBG: upArrowURL,
            downArrowBG: downArrowURL,
            betTypeFontSize: "1.25rem"
        }
    },
    computed: {
        betTypeStyle() {
            return {
                '--font-size': this.betTypeFontSize,
            }
        }
    },
    props: {
        prop_MatchItems: Object,
    },
    methods: {
        itemHovered() {
                this.betTypeFontSize = "1.5rem"
                //console.log("hovered") *note: hover is fired many times (bad)
            },
        itemOut() {
                this.betTypeFontSize = "1.25rem"
                //console.log("out")
            }
    },
    mounted() { //onLoad event
        //console.log(this.prop_MatchItems.constructor.name)
    }
}

</script>
