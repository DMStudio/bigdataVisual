<template>
  <div id='histogram' style="margin-top: 120px;margin-left: 100px">
  </div>
</template>
<script lang='babel'>
  import echarts from 'echarts'

  export default {
    data () {
      return {
        itemStyle: {
          emphasis: {
            barBorderWidth: 1,
            shadowBlur: 10,
            shadowOffsetX: 0,
            shadowOffsetY: 0,
            shadowColor: 'rgba(0,0,0,0.5)'
          }
        }
      }
    },
    mounted () {
      var histogram = echarts.init(document.getElementById('histogram'))
      var 亿 = {
        normal: {
          position: 'right'
        }
      }
      histogram.setOption({
        legend: {
          data: ['总待收']
        },
        title: {
          text: '交错正负轴标签',
          subtext: 'From ExcelHome'
        },
        tooltip: {
          trigger: 'axis',
          axisPointer: {            // 坐标轴指示器，坐标轴触发有效
            type: 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
          }
        },
        grid: {
          top: 80,
          bottom: 30
        },
        yAxis: {
          type: 'value',
          position: 'top',
          splitLine: {lineStyle: {type: 'dashed'}},
          axisLabel: {
            formatter: '{value} 亿'
          }
        },
        xAxis: {
          type: 'category',
          axisLine: {show: false},
          axisTick: {show: false},
          splitLine: {show: false},
          axisLabel: {
            formatter: '{value}'
          },
          data: ['2月', '3月', '4月', '5月', '6月', '7月']
        },
        series: [
          {
            name: '总待收',
            type: 'bar',
            stack: '总量',
            label: {
              normal: {
                show: false
              }
            },
            color: ['#008080'],
            data: [
              {value: 2.52, label: 亿},
              {value: 2.47, label: 亿},
              {value: 2.53, label: 亿},
              {value: 2.57, label: 亿},
              {value: 2.86, label: 亿},
              {value: 3.1, label: 亿}
            ]
          }
        ]
      })
    }
  }
</script>
<style>
  #histogram {
    width: 1000px;
    height: 500px;
  }
</style>
