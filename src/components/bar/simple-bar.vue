
<template>
    <echarts :width="500" :height="400" :options="options" />
</template>

<script>
/* eslint-disable */
import echarts from "../echarts"
import 'echarts/lib/component/tooltip'
import 'echarts/lib/chart/bar'
import 'echarts/lib/component/title'

export default {
  props: {
    titleOption: {
      type: Object,
      default: () => ({})
    },
    legendVisible: {
      type: Boolean,
      default: true
    },
    titleVisible: {
      type: Boolean,
      default: false
    },
    title: String,
    data: Object
  },
  data: function() {
    return {
      options: {
        title: Object.assign({}, this.titleOption, {
          text: this.title,
          show: this.titleVisible
        }),
        tooltip: {},
        legend: {
          show: this.legendVisible,
          data: this.data.columns || []
        },
        yAxis: {
          type: 'value'
        },
        xAxis: {
          type: 'category',
          data: this.data.columns || []
        },
        series: [
          {
            type: "bar",
            data: this.data.rows || []
          }
        ]
      }
    };
  },
  components: { echarts },
  created() {
    // 数据变化，传递到底层
    this.$watch('data', function(newVal, oldVal) {
      this.options.xAxis.data = newVal.columns
      this.options.legend.data = newVal.columns || []
      this.options.series = [{
        type: "bar",
        data: this.data.rows || []
      }]
    }, { deep: true })
  }
};
</script>
