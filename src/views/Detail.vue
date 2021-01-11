<style lang="scss" scoped>

.main_card-wrap {
    min-height: 7rem;
    //min-width: 23.5rem;
    display: flex;
    flex-direction: column;
    margin: 0rem 1.5rem 0rem 1.5rem;
    background-color: #fff;
    border-radius: 0.75rem 0.75rem 0.75rem 0;
    .main_info {
        display: flex;
        flex-direction: row;
        margin: 1.5rem 0 0 1.5rem;
        min-height: 3.5rem;
        .ico_transaction {
            width: 3.5rem;
            height: 3.5rem;
            background-color: #eee;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 0.75rem 0.75rem 0 0.75rem;
            .icon {
                width: 2.5rem;
                height: 2.5rem;
                background-size: contain;
            }
            .icon_deposit {
                background-image: url("../assets/icons/outline/branded/deposit-sm.png");
            }
            .icon_withdrawal {
                background-image: url("../assets/icons/outline/branded/withdrawal-sm.png");
            }
            .icon_transfer {
                background-image: url("../assets/icons/outline/branded/transfer-sm.png");
            }
        }
        .transaction-heading {
            margin-left: 1rem;
            display: flex;
            flex-direction: column;
            justify-content: center;
            & div:nth-child(1) {
                color: #11111160;
                font-size: 0.75rem;
            }
            & div:nth-child(2) {
                font-size: 1.5rem;
            }
        }
    }
    .subinfo {
        display: flex;
        flex-direction: row;
        margin: 2rem 0 0 1.5rem;
        align-items: center;
        flex-wrap: wrap;
        .status {
            & div:nth-child(1) {
                color: #11111160;
                font-size: 0.75rem;
            }
            & div:nth-child(2) {
                text-transform: uppercase;
                margin-top: 0.25rem;
            }
        }
        .lastupdate {
            margin-left: 1rem;
            & div:nth-child(1) {
                color: #11111160;
                font-size: 0.75rem;
            }
            & div:nth-child(2) {
                margin-top: 0.25rem;
            }
        }
        .urge-wrap {
            flex-grow: 2;
            margin-left: 2rem;
            display: flex;
            flex-direction: row;
            justify-content: flex-end;
            padding-right: 1.5rem;
            .urge-contents {
                min-width: 6rem;
                min-height: 3.5rem;
                background-color: #ff8800;
                border-radius: 1.5rem 1.5rem 1.5rem 0;
                display: flex;
                flex-direction: row;
                justify-content: center;
                align-items: center;
                & div:nth-child(1) {
                    font-weight: bold;
                }
                & div:nth-child(2) {
                    width: 1.5rem;
                    height: 1.5rem;
                    margin-left: 0.375rem;
                    background-image: url("../assets/icons/outline/arrow_right-sm-blk.png");
                    background-size: contain;
                }
            }
        }
    }
    .bar {
        display: flex;
        justify-content: center;
        margin: 1.5rem;
        & div:nth-child(1) {
            background-color: #eee;
            width: 100%;
            height: 0.75rem;
            border-radius: 0.75rem 0.75rem 0.75rem 0;
            padding: 0 0.25rem;
            display: flex;
            align-items: center;
            & div:nth-child(1) {
                background-color: #888;
                height: 0.25rem;
            }
        }
    }
}

.main_card-shadow {
    margin: 0 2.5rem 0 2.5rem;
    //min-width: 20.5rem;
    min-height: 1rem;
    background-color: #11111160;
    border-radius: 0 0 0.75rem 0;
}

.conv_exchange {
    //min-width: 20.5rem;
    background-color: #444;
    border-radius: 0.75rem 0.75rem 0.75rem 0;
    margin: .75rem 1.5rem 0rem 1.5rem;
    padding: 1.5rem;
    color: #eeeeee60;
    & div:nth-child(1) {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }
    .remarks {
        margin-top: 1.5rem;
    }
}

@media only screen and (min-width: 680px) {
    .top_info {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }
}

@media only screen and (min-width: 440px) {
    .main_card-wrap {
        .subinfo {
            .urge-wrap {
                .urge-contents {
                    min-width: 8rem;
                }
            }
        }
    }
}

@media only screen and (max-width: 440px) {
    .main_card-wrap {
        .subinfo {
          .status {
              & div:nth-child(2) {
                  font-size: 0.875rem;
              }
          }
          .lastupdate {
              & div:nth-child(2) {
                  font-size: 0.875rem;
              }
          }
            .urge-wrap {
              margin: 0;
                .urge-contents {
                  min-width: 0;
                    .urge-label{
                      display: none;
                    }
                    & div:nth-child(2) {
                        margin: 0 1rem;
                      }
                }
            }
        }
    }
}

</style>

<template>
<DetailHeader :prop_transactionType="prop_txnType" />
<div class="main_card-wrap">
    <div class="top_info">
        <div class="main_info">
            <div class="ico_transaction">
                <div class="icon" :class="getTxnIcon()"></div>
            </div>
            <div class="transaction-heading">
                <div>
                    {{getTxnPrefix()}}{{randomizeRange(10000000,99000000)}}
                </div>
                <div>{{ `${getSign()} ${prop_txnCurrency} ${(prop_txnValue)}` }}</div>
            </div>
        </div>
        <div class="subinfo">
            <div class="status">
                <div>Current Status</div>
                <div :class="{'txtTomato': prop_txnStatus=='failed','txtOrange': prop_txnStatus=='pending'}">{{ prop_txnStatus }}</div>
            </div>
            <div class="lastupdate">
                <div>Last Updated</div>
                <div>{{`${prop_txnDateStamp} mins ago` }}</div>
            </div>
            <div v-if="checkUrge(prop_txnStatus)" class="urge-wrap">
                <div class="urge-contents">
                    <div class="urge-label">Urge!</div>
                    <div></div>
                </div>
            </div>
            <div v-else style="width:2rem"></div>
        </div>
    </div>
    <div class="bottom_info">
        <div v-if="checkUrge(prop_txnStatus)" class="bar">
            <div>
                <!--outer bar-->
                <div :style="{ width: `${prop_txnDateStamp}%`}"></div>
                <!--inner bar-->
            </div>
        </div>
        <div v-else style="height:1.5rem"></div>
    </div>
</div>
<div class="main_card-shadow"></div>
<div class="conv_exchange" v-for="(item, index) in convDetails" :key="index">
    <div>
        <div>{{item.action}}</div>
        <div v-if="item.timeStamp > 10">{{item.timeStamp}} min ago</div>
        <div v-else>Moments ago...</div>
    </div>
    <div v-if="item.remarks!=''" class="remarks">Remarks: {{item.remarks}}</div>
</div>

</template>

<script>

// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'
import {
    useRoute // this is declared so that you can use this.route.params.txnSomething... that comes from router.push
}
from 'vue-router';
import DetailHeader from './../components/common/DetailHeader.vue'
export default {
    name: 'Detail',
    data() {
        return {
            route: useRoute(), //params can be passed on this object
            convDetails: [],
            convActions: ["Upload (Manual)", "Make Deposit", "Wait for confirmation", "Receipt Accepted", "Receipt Submitted"],
            convRemarks: ["If set to 0, the extra space around content isn’t factored in. If set to auto, the extra space is distributed based on its flex-grow value. See this graphic.", "It is recommended that you use this shorthand property rather than set the individual properties. The shorthand sets the other values intelligently.", "This defines the default size of an element before the remaining space is distributed.", "It can be a length (e.g. 20%, 5rem, etc.) or a keyword. The auto keyword means “look at my width or height property” (which was temporarily done by the main-size keyword until deprecated).", "", "", ""],
            convTimeStamp: []
        }
    },
    props: {
        prop_txnCurrency: String,
        prop_txnValue: String,
        prop_txnDateStamp: String,
        prop_txnStatus: String,
        prop_txnType: String,
        prop_txnId: String
    },
    computed: {

    },
    components: {
        DetailHeader
    },
    methods: {
        toInt(number) {
                return Intl.NumberFormat().format(parseInt(number))
            },
            getSign() {
                return this.prop_txnType == 'deposit' ? '+' : this.prop_txnType == 'withdrawal' ? '-' : '>'
            },
            getTxnIcon() {
                return {
                    'icon_deposit': this.prop_txnType == 'deposit',
                    'icon_withdrawal': this.prop_txnType == 'withdrawal',
                    'icon_transfer': this.prop_txnType == 'transfer'
                }
            },
            getTxnPrefix() {
                return this.prop_txnType == 'deposit' ? 'DP' : this.prop_txnType == 'withdrawal' ? 'WD' : 'TN'
            },
            checkUrge(status) {
                return (status == 'pending' || status == 'processing')
            },
            randomizeRange(lowerLimit, upperLimit) {
                return Math.floor(Math.random() * upperLimit) + lowerLimit
            },
            randomize(limit) {
                return Math.floor(Math.random() * limit)
            },
            addMoreDetails(i) {
                var actionIndex = this.randomize(this.convActions.length)
                var remarksIndex = this.randomize(this.convRemarks.length)
                if (!(this.convDetails.some(detail => detail.action === this.convActions[actionIndex]))) {
                    this.convDetails.push({
                        action: this.convActions[actionIndex],
                        remarks: this.convRemarks[remarksIndex],
                        timeStamp: this.convTimeStamp[i]
                    })
                }
            }
    },
    mounted() {
      //console.log(this.route.params.fullTxnDetails) // pass object as parameter, fail
      //console.log(this.fullTxnDetails) // pass object as props, fail
    },
    created() {
        var i = 0
        var limit = this.randomize(5) + 1
        for (i = 0; i < limit; i++) {
            this.convTimeStamp.push(this.randomize(60))
        }
        this.convTimeStamp.sort(function(a, b) {
            return a - b
        })
        for (i = 0; i < limit; i++) {
            this.addMoreDetails(i)
        }
        //console.clear()
            //console.table(this.convDetails)
            //this.transactionData = this.route.params.data
    }
}

</script>
