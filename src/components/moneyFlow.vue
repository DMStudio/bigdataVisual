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
      var labelRight = {
        normal: {
          position: 'right'
        }
      }
      histogram.setOption({
        legend: {
          data: ['现金流']
        },
        title: {
          text: '交错正负轴标签',
          subtext: 'From ExcelHome',
          sublink: 'http://e.weibo.com/1341556070/AjwF2AgQm'
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
          splitLine: {lineStyle: {type: 'dashed'}}
        },
        xAxis: {
          type: 'category',
          axisLine: {show: false},
          axisLabel: {show: false},
          axisTick: {show: false},
          splitLine: {show: false},
          data: ['2月', '3月', '4月', '5月', '6月', '7月']
        },
        series: [
          {
            name: '现金流',
            type: 'bar',
            stack: '总量',
            label: {
              normal: {
                show: false
              }
            },
            color: ['#008080'],
            data: [
              {value: 2267.76, label: labelRight},
              {value: -458.89, label: labelRight},
              {value: 623.63, label: labelRight},
              {value: 260.78, label: labelRight},
              {value: 2213.83, label: labelRight},
              {value: 2214.99, label: labelRight}
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
