<template>
    <div class="converter">
        <conver-item @update:selected="onUpdateSelected" :exchange-data="exchangeData.CNY" country="CNY">

        </conver-item>
        <conver-item @update:selected="onUpdateSelected" :exchange-data="exchangeData.USD" country="USD"></conver-item>
        <conver-item @update:selected="onUpdateSelected" :exchange-data="exchangeData.EUR" country="EUR"></conver-item>
        <conver-item @update:selected="onUpdateSelected" :exchange-data="exchangeData.CAD" country="CAD"></conver-item>
        <conver-item @update:selected="onUpdateSelected" :exchange-data="exchangeData.HKD" country="HKD"></conver-item>
        <conver-item @update:selected="onUpdateSelected" :exchange-data="exchangeData.ARS" country="ARS"></conver-item>
        <conver-item @update:selected="onUpdateSelected" :exchange-data="exchangeData.AUD" country="AUD"></conver-item>
    </div>
</template>

<script>
    import converItem from './conver-items';
    import axios from 'axios';

    const BASE_URL = 'https://v3.exchangerate-api.com/bulk/f177173bcb6a03a5274a7f95/';
    export default {
        name: 'converter',
        components: {
            'conver-item': converItem
        },
        props: {
            selected: {
                type: String
            }
        },
        data() {
            return {
                exchangeData: '加载中',
                $selected: this.selected
            }
        },
        mounted() {
            axios.get(BASE_URL + this.selected).then((res) => {
                this.exchangeData = res.data.rates;
            })
        },
        methods: {
            onUpdateSelected(newSelected) {

                this.$emit('update:selected', newSelected);
                this.$nextTick(function () {
                    this.updateData();
                })


            },
            updateData() {

                axios.get(BASE_URL + this.selected).then((res) => {
                    this.exchangeData = res.data.rates;
                })
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    .converter {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
</style>
