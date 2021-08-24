<template>
  <common-card title="今日交易用户数"
               value="81014">
    <template>
      <v-chart :options="getOptions()" />
    </template>
    <template v-slot:footer>
      <span>退货率 </span>
      <span class="emphasis">11111</span>
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
          data: ['00:00', '01:00', '02:00', '03:00', '04:00', '05:00', '06:00', '07:00', '08:00', '09:00', '10:00', '11:00', '12:00', '13:00'],
          show: false
        },
        yAxis: {
          show: false
        },
        series: [{
          type: 'bar',
          name: '用户实时交易量',
          data: [410, 82, 200, 334, 390, 330, 220, 150, 82, 200, 134, 290, 330, 150],
          // 修改柱子宽度
          barWidth: '60%'
        }],
        color: ['#3398DB'],
        tooltip: {},
        grid: {
          top: 0,
          left: 0,
          bottom: 0,
          right: 0
        }
      }
    }
  }
}
</script>

<style scoped>
</style>
