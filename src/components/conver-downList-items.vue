<template>

        <div class="item" >
            <img class="item-img" :src="flagSrc" @click="" alt="">
            {{ZHname}} {{country}}
        </div>


</template>

<script>
    import ZHlist from '../assets/ZHLIST'

    const defaultSrc = "./image/";
    export default {
        name: "conver-downList-items",
        props: {
            country: {
                type: String
            }
        },
        data() {
            return {
                ZHname: ''
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
    }
</script>

<style lang="scss" scoped>
    .item {
        display: flex;
        align-items: center;
        font-size: 12px;
        border-bottom: 1px solid #ddd;
        .item-img {
            height: 1rem;
        }
    }
</style>