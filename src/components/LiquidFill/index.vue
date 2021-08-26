<template>
  <ve-liquidfill :data="chartData"
                 height="100%"
                 :settings="chartSetting"></ve-liquidfill>
</template>

<script>
export default {
  data() {
    return {
      chartData: {
        columns: ['title', 'percent'],
        rows: [{
          title: '用户增长率',
          percent: 0.68
        }]
      },
      chartSetting: {
        seriesMap: {
          用户增长率: {
            // 修改半径
            radius: '80%'
          }
        }
      }
    }
  }
}
</script>

<style scoped>
</style>
