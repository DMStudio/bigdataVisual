<template>
  <div>
    <div style="position:fixed;top: 80px;width: 100%;height: 100%">
      <div class="chart" id="homeChart" style="width:100%;height:90%;margin-right: -100px"></div>
    </div>
  </div>
</template>

<script>
  import echarts from 'echarts'

  export default{
    name: 'Home',
    data () {
      return {
        msg: 'oh mygod'
      }
    },
    mounted () {
      var myChart = echarts.init(document.getElementById('homeChart'))
      myChart.setOption({
        tooltip: {
          trigger: 'axis',
          axisPointer: {            // 坐标轴指示器，坐标轴触发有效
            type: 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
          }
        },
        legend: {
          data: ['新增投资人数', '新增借款人数', '新增交易人数']
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        xAxis: [
          {
            type: 'category',
            data: ['二月', '三月', '四月', '五月', '六月', '七月']
          }
        ],
        yAxis: [
          {
            type: 'value'
          }
        ],
        series: [
          {
            name: '新增投资人数',
            type: 'bar',
            stack: 'people1',
            barWidth: 40,
            color: ['#008080'],
            data: [3443, 4259, 4088, 4891, 4297, 4397]
          },
          {
            name: '新增借款人数',
            type: 'bar',
            stack: 'people1',
            color: ['#87cecb'],
            data: [722, 1053, 1008, 1053, 1185, 1421]
          },
          {
            name: '新增交易人数',
            type: 'bar',
            stack: 'allPeople',
            barWidth: 40,
            color: ['#4682b4'],
            data: [4165, 5312, 5096, 5944, 5482, 5818]
          }
        ]
      })
    }
  }
</script>
