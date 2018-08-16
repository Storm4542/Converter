<template>
    <div>
        <converter :selected.sync="selected"></converter>
    </div>
</template>

<script>
    import Converter from './components/converter.vue'

    export default {
        name: 'app',
        components: {
            Converter
        },
        data() {
            return {
                selected: 'USD'
            }
        }
    }
</script>

<style lang="scss">

</style>
