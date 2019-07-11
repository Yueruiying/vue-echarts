<template>
    <echarts :options="options" />
</template>

<script>
/* eslint-disable */
import echarts from "../echarts"
import 'echarts/lib/component/tooltip'
import 'echarts/lib/chart/bar'
import 'echarts/lib/component/title'

export default {
    data: function() {
        return {
            options: {}
        }
    },
    components: { echarts }    
}
</script>

