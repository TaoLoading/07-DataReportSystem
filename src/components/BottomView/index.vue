<template>
  <div class="bottom-view">
    <!-- 关键词搜索信息展示区 -->
    <div class="view">
      <el-card shadow="hover">
        <template v-slot:header>
          <div class="title-wrapper">关键词搜索</div>
        </template>
        <template>
          <div class="chart-wrapper">
            <!-- 搜索信息表表图展示区 -->
            <div class="chart-inner">
              <div class="chart">
                <div class="chart-title">搜索用户数</div>
                <div class="chart-data">111</div>
                <v-chart :options="searchUserOption" />
              </div>
              <div class="chart">
                <div class="chart-title">搜索量</div>
                <div class="chart-data">222</div>
                <v-chart :options="searchUserOption" />
              </div>
            </div>
            <!-- 搜索信息表格展示区 -->
            <div class="table-wrapper">
              <el-table :data="tableData">
                <el-table-column prop="rank"
                                 label="排名" />
                <el-table-column prop="keyword"
                                 label="关键词" />
                <el-table-column prop="count"
                                 label="总搜索量" />
                <el-table-column prop="users"
                                 label="搜索用户数" />
                <el-table-column prop="range"
                                 label="搜索占比" />
              </el-table>
              <el-pagination layout="prev, pager, next"
                             :total="100"
                             :page-size="4"
                             background
                             @current-change="onPageChange" />
            </div>
          </div>
        </template>
      </el-card>
    </div>
    <!-- 销售数据类别信息展示区 -->
    <div class="view">
      <el-card shadow="hover">
        <template v-slot:header>
          <div class="title-wrapper">
            <div class="title">分类销售排行</div>
            <div class="radio-wrapper">
              <el-radio-group v-model="radioSelect"
                              size="small"
                              @current-change="onCategoryChange">
                <el-radio-button label="品类"></el-radio-button>
                <el-radio-button label="商品"></el-radio-button>
              </el-radio-group>
            </div>
          </div>
        </template>
        <!-- 类别信息表图展示区 -->
        <template>
          <div class="chart-wrapper">
            <v-chart :options="categoryOptions" />
          </div>
        </template>
      </el-card>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      radioSelect: '品类',
      categoryOptions: {},
      searchUserOption: {
        xAxis: {
          type: 'category',
          boundaryGap: false
        },
        yAxis: {
          show: false
        },
        series: [
          {
            type: 'line',
            data: [100, 200, 280, 100, 200, 280, 100, 200, 280],
            areaStyle: {
              color: 'rgba(95,187,255,.5)'
            },
            lineStyle: {
              color: 'rgb(95,187,255)'
            },
            itemStyle: {
              opacity: 0
            },
            smooth: true
          }
        ],
        grid: {
          top: 0,
          left: 0,
          bottom: 0,
          right: 0
        }
      },
      searchNumberOption: {},
      tableData: [
        {
          id: 1, rank: 1, keyword: '北京', count: 100, users: 90, range: '90%'
        },
        {
          id: 2, rank: 2, keyword: '北京', count: 100, users: 90, range: '90%'
        },
        {
          id: 3, rank: 3, keyword: '北京', count: 100, users: 90, range: '90%'
        },
        {
          id: 4, rank: 4, keyword: '北京', count: 100, users: 90, range: '90%'
        }
      ]
    }
  },
  methods: {
    onPageChange(page) {
      console.log(page)
    },
    onCategoryChange(page) {
      console.log(page)
    },
    // 饼图
    renderPieChart() {
      const mockData = [
        {
          legendname: '粉面粥店',
          value: 67,
          percent: '15.40%',
          name: '粉面粥店 | 15.40%'
        },
        {
          legendname: '简餐便当',
          value: 97,
          percent: '22.30%',
          name: '简餐便当 | 22.30%'
        },
        {
          legendname: '汉堡披萨',
          value: 92,
          percent: '21.15%',
          name: '汉堡披萨 | 21.15%'
        }
      ]
      this.categoryOptions = {
        title: [
          // 主标题
          {
            text: '品类分布',
            textStyle: {
              fontSize: 14,
              color: '#666'
            },
            left: 20,
            top: 20
          },
          // 副标题
          {
            text: '累计订单量',
            subtext: '320',
            x: '34.5%',
            y: '43.8%',
            textAlign: 'center',
            textStyle: {
              fontSize: 14,
              color: '#999'
            },
            subtextStyle: {
              fontSize: 28,
              color: '#333'
            }
          }
        ],
        series: [
          {
            type: 'pie',
            data: mockData,
            label: {
              normal: {
                show: true,
                formatter: function (params) {
                  return params.data.legendname
                }
              }
            },
            // 修改圆心位置
            center: ['35%', '50%'],
            // 修改内外半径，实现空心圆
            radius: ['45%', '60%'],
            // 修改连接线样式
            labelLine: {
              normal: {
                length: 5,
                length2: 3,
                smooth: true
              }
            },
            // 排序规则
            clockwise: false,
            itemStyle: {
              // 添加边距
              borderWidth: 4,
              borderColor: '#fff'
            }
          }
        ],
        // 图例
        legend: {
          // 可以滑动
          type: 'scroll',
          // 竖向排列
          orient: 'vertical',
          height: 250,
          left: '70%',
          top: 'middle',
          textStyle: {
            color: '#8c8c8c'
          }
        },
        tooltip: {
          trigger: 'item',
          // 对提示信息进行定制
          formatter: function (params) {
            const str = params.marker + params.data.legendname + '<br />' + '数量：' + params.data.value + '<br />' + '占比：' + params.data.percent
            return str
          }
        }
      }
    }
  },
  mounted() {
    this.renderPieChart()
  }
}
</script>

<style lang="scss" scoped>
.bottom-view {
  display: flex;
  margin-top: 20px;
  .view {
    flex: 1;
    width: 50%;
    box-sizing: border-box;
    &:first-child {
      padding: 0 10px 0 0;
    }
    &:last-child {
      padding: 0 0 0 10px;
    }
    .title-wrapper {
      display: flex;
      align-items: center;
      height: 60px;
      box-sizing: border-box;
      border-bottom: 1px solid #eee;
      font-size: 14px;
      font-weight: 500;
      padding: 0 0 0 20px;
      .radio-wrapper {
        flex: 1;
        display: flex;
        justify-content: flex-end;
        padding-right: 20px;
      }
    }
    .chart-wrapper {
      display: flex;
      flex-direction: column;
      height: 452px;
      .chart-inner {
        display: flex;
        padding: 0 10px;
        margin-top: 20px;
        .chart {
          flex: 1;
          padding: 0 10px;
          .chart-title {
            color: #999;
            font-size: 14px;
          }
          .chart-data {
            font-size: 22px;
            color: #333;
            font-weight: 500;
            letter-spacing: 2px;
          }
          .echarts {
            height: 50px;
          }
        }
      }
      .table-wrapper {
        flex: 1;
        margin-top: 20px;
        padding: 0 20px 20px;
        .el-pagination {
          display: flex;
          justify-content: flex-end;
          margin-top: 15px;
        }
      }
    }
  }
}
</style>
