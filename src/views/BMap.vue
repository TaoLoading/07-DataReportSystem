<template>
  <!-- 使用ECharts绘制百度地图 -->
  <v-chart :options="options"></v-chart>
</template>

<script>
import 'echarts/extension/bmap/bmap'
const points = [
  {
    name: '济南',
    value: [117.120075, 36.659565, 180]
  },
  {
    name: '青岛',
    value: [120.384859, 36.096261, 150]
  },
  {
    name: '北京',
    value: [116.403039, 39.914245, 300]
  },
  {
    name: '重庆',
    value: [106.557287, 29.56221, 100]
  },
  {
    name: '上海',
    value: [121.479965, 31.236176, 200]
  },
  {
    name: '拉萨',
    value: [91.143963, 29.657729, 50]
  },
  {
    name: '西安',
    value: [108.94819, 34.347984, 120]
  },
  {
    name: '成都',
    value: [104.038986, 30.603334, 170]
  },
  {
    name: '武汉',
    value: [114.304678, 30.698774, 180]
  },
  {
    name: '长沙',
    value: [112.906483, 28.284642, 150]
  }
]
const pointsMy = [{
  name: '济南',
  value: [117.120075, 36.659565, 180]
}]

export default {
  data() {
    return {
      options: {}
    }
  },
  mounted() {
    this.options = {
      // 标题
      title: {
        text: '销售数据大盘',
        subtext: '销售趋势统计',
        left: 'center'
      },
      // 地图
      bmap: {
        key: '4wIObEcAFFekF9IGauieRxKvINCFSCsQ',
        center: [104.114129, 37.550339],
        zoom: 5,
        // 是否允许缩放
        roam: true
      },
      // 提示信息
      tooltip: {},
      // 点
      series: [
        {
          name: '销售额',
          type: 'scatter',
          coordinateSystem: 'bmap',
          data: points,
          encode: {
            // 修改tooltip显示的数据为第三个数据
            value: 2
          },
          itemStyle: {
            color: 'purple'
          },
          // 点的大小
          symbolSize: function (val) {
            return val[2] / 10
          }
        },
        {
          name: '销售额',
          type: 'effectScatter',
          coordinateSystem: 'bmap',
          data: pointsMy,
          encode: {
            // 修改tooltip显示的数据为第三个数据
            value: 2
          },
          itemStyle: {
            color: 'purple'
          },
          // 点的大小
          symbolSize: function (val) {
            return val[2] / 10
          },
          hoverAnimation: true,
          // 波纹效果
          rippleEffect: {
            brushType: 'stroke'
          }
        }
      ]
    }
  }
}
</script>

<style scoped>
</style>
