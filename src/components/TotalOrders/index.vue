<template>
  <common-card title="累计订单量"
               :value="666666">
    <template>
      <v-chart :options="getOptions()" />
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
  methods: {
    getOptions() {
      return {
        xAxis: {
          type: 'category',
          show: false,
          // 取消默认距x轴的距离
          boundaryGap: false
        },
        yAxis: {
          show: false
        },
        series: [{
          type: 'line',
          data: [620, 432, 220, 534, 709, 430, 220, 320, 532, 320, 834, 690, 530, 220, 620],
          // 显示面积
          areaStyle: {
            color: 'purple'
          },
          lineStyle: {
            width: 0
          },
          itemStyle: {
            opacity: 0
          },
          // 平滑显示
          smooth: true
        }],
        // 左右边距置为0
        grid: {
          top: 0,
          bottom: 0,
          left: 0,
          right: 0
        }
      }
    }
  }
}
</script>

<style scoped>
</style>
