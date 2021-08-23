<template>
  <div class="common-card">
    <div class="title">1</div>
    <div class="value">2</div>
    <div class="chart">3</div>
    <div class="line">4</div>
    <div class="total">5</div>
  </div>
</template>

<script>
export default {
  name: 'CommonCard'
}
</script>

<style scoped>
.title {
  font-size: 12px;
  color: #999;
}
.value {
  font-size: 25px;
  color: #000;
  margin-top: 5px;
  letter-spacing: 1px;
}
.chart {
  height: 50px;
}
.line {
  margin: 10px 0;
  border-top: 1px solid #eee;
}
.total {
  font-size: 12px;
  color: #666;
}
</style>
