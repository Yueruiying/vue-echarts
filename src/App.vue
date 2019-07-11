
<template>
  <div>
    <simple-bar :width="500" :height="400" :data="chartData" />
    <stack-bar :width="500" :height="400" :data="chartData" />
  </div>
</template>

<script>
/* eslint-disable */
import SimpleBar from './components/bar/simple-bar'
import StackBar from './components/bar/stack-bar'
export default {
  components: { SimpleBar, StackBar },
  data: function() {
    return {
      chartData: {}
    }
  },
  methods: {
    getData() {
      // 支持异步数据
      setTimeout(() => {
        this.chartData = {
          columns: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"],
          rows: [9, 20, 36, 10, 10, 20]
        }
      }, 200)
    }
  },
  created() {
    this.getData()
  }
}
</script>
