<template>
    <div class="downList">
        <downlist-item country="CNY"></downlist-item>
        <downlist-item country="USD"></downlist-item>
        <downlist-item country="EUR"></downlist-item>
        <downlist-item country="CAD"></downlist-item>
        <downlist-item country="ARS"></downlist-item>
        <downlist-item country="HKD"></downlist-item>
        <downlist-item country="AUS"></downlist-item>
    </div>
</template>

<script>
    import downlistItem from './conver-downList-items'
    export default {
        name: "conver-downList",
        props:{
            country:{
                type:String
            }
        },
        components:{
            downlistItem
        }
    }
</script>

<style lang="scss" scoped>
    .downList {
        border: 1px orange solid;
        background: #fff;


    }
</style>