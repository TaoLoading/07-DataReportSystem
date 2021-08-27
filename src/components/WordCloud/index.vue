<template>
  <ve-wordcloud :data="data"
                height="100%"></ve-wordcloud>
</template>

<script>
export default {
  name: '',
  data() {
    return {
      data: {
        columns: ['name', 'value'],
        rows: [
          {
            name: '土豆炖牛肉', value: 66
          },
          {
            name: '肉丝面', value: 80
          },
          {
            name: '黄焖鸡', value: 50
          },
          {
            name: '甜点', value: 60
          },
          {
            name: '水饺', value: 70
          },
          {
            name: '烤鸭', value: 50
          },
          {
            name: '奶茶', value: 100
          }
        ]
      }
    }
  },
  methods: {

  }
}
</script>

<style scoped>
</style>
