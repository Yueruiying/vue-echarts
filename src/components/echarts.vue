<template>
    <div ref="container"></div>
</template>

<script>
/* eslint-disable */
import echarts from 'echarts/lib/echarts'
export default {
    props: {
        width: {
            type: Number,
            default: 500
        },
        height: {
            type: Number,
            default: 400
        },
        options: Object
    },
    charts: null,
    mounted() {
        this.$refs.container.style.width = this.width + 'px'
        this.$refs.container.style.height = this.height + 'px'
        this.charts = echarts.init(this.$refs.container)                                                                         
        this.charts.setOption(this.options)
    },
    created() {
        this.$watch('options', (newVal, oldVal) => {
            this.charts.setOption(newVal)
        }, { deep: true })
    }
}
</script>

