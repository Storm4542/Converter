<template>
    <div class="conver-item" @click="changeCountry">
        <div class="Country">
            <div class="flag" @click="downListVisable = !downListVisable">
                <img class=flag-img :src="flagSrc" alt="">
                <span>{{country}}</span>
            </div>
            <!--<cover-down-list :country="country" v-if="downListVisable" class="downList"></cover-down-list>-->
        </div>
        <slot></slot>
        <div class="money">
            <p>{{exchangeData}}</p>
            <!--<input class="money-input" :value="exchangeData" type="text">-->
            <p>{{ZHname}}</p>
        </div>
    </div>
</template>u

<script>
    import DownList from './conver-downList'
    import ZHlist from '../assets/ZHLIST'

    const defaultSrc = "./image/";
    export default {
        name: "conver-items",
        props: {
            country: {
                type: String
            },
            exchangeData: {
                type: Number
            },
            selected: {
                type: String
            }
        },
        components: {
            'cover-down-list': DownList
        },

        data() {
            return {
                message: 1,
                downListVisable: false,
                value: 1,
                ZHname: '',
            }
        },
        computed: {
            flagSrc() {
                return defaultSrc + this.country + '.png'
            }
        },
        mounted() {
            ZHlist.forEach((item) => {
                if (item.name === this.country) {
                    this.ZHname = item.cover
                }
            })
        },
        methods: {
            changeCountry() {
                this.$emit('update:selected', this.country);

            }
        }
    }
</script>

<style lang="scss" scoped>
    .conver-item {
        height: 2rem;
        width: 9.5rem;
        margin: .3rem 0;
        display: flex;
        justify-content: space-between;
        align-items: center;
        border-bottom: 1px solid #ddd;
        .Country {
            position: relative;
            .flag {
                display: flex;
                align-items: center;
                .flag-img {
                    padding: .1rem 0;
                    height: 1.8rem;
                }
                span {
                    font-size: 20px;
                }
            }
            .downList {
                position: absolute;
                top: 100%;
                left: 0;
                z-index: 1;
                width: 9.5rem;
            }

        }
        .money {
            text-align: right;
            .money-input {
                width: 2rem;
            }
            .money-input:focus {
                outline: none;
            }
        }
    }
</style>