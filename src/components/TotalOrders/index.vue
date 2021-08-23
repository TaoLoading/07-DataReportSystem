<template>
  <common-card title="累计订单量"
               :value="666666">
    <template>
      <!-- <v-chart :options="getOptions()" /> -->
      <div id="total-orders-chart"
           :style="{width:'100%',height:'100%'}"></div>
    </template>
    <template v-slot:footer>
      <span>昨日订单量 </span>
      <span class="emphasis">1111111111</span>
    </template>
  </common-card>
</template>

<script>
import commonCardMixin from '../../mixins/commonCardMixin'
export default {
  mixins: [commonCardMixin],
  mounted() {
    const chartDom = document.getElementById('total-orders-chart')
    const chart = this.$echarts.init(chartDom)
    chart.setOption({
      xAxis: {
        type: 'category',
        show: false
      },
      yAxis: {
        show: false
      },
      series: [{
        type: 'line',
        data: [620, 432, 100, 200, 300, 512, 435]
      }]
    })
  }
  /* methods: {
    getOptions() {
      return this.orderTrend.length > 0 ? {
        xAxis: {
          type: 'category',
          show: false,
          boundaryGap: false
        },
        yAxis: {
          show: false
        },
        series: [{
          type: 'line',
          data: this.orderTrend,
          areaStyle: {
            color: 'purple'
          },
          lineStyle: {
            width: 0
          },
          itemStyle: {
            opacity: 0
          },
          smooth: true
        }],
        grid: {
          top: 0,
          bottom: 0,
          left: 0,
          right: 0
        }
      } : null
    }
  } */
}
</script>

<style scoped>
</style>
