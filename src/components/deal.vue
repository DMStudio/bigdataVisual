<template>
  <div id='histogram'>

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
      histogram.setOption({
        legend: {
          data: ['月成交量', '累计成交量']
        },
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'cross',
            label: {
              backgroundColor: '#283b56'
            }
          }
        },
        toolbox: {
          show: true,
          feature: {
            dataView: {readOnly: false},
            restore: {},
            saveAsImage: {}
          }
        },
        xAxis: {
          data: ['2月', '3月', '4月', '5月', '6月', '7月']
        },
        yAxis: [{
          type: 'value',
          scale: true,
          min: 0,
          splitLine: {
            lineStyle: {
              type: 'dashed'
            }
          },
          axisLabel: {
            formatter: '{value} 万元'
          }
        }, {
          type: 'value',
          scale: true,
          min: 0,
          splitNumber: 4,
          boundaryGap: [0.01, 0.01],
          splitLine: {
            lineStyle: {
              type: 'dashed'
            }
          },
          axisLabel: {
            formatter: '{value} 亿元'
          }
        }],
        color: ['#547B95', '#CD6C4A'],
        series: [{
          name: '月成交量',
          type: 'bar',
          yAxisIndex: 0,
          itemStyle: this.itemStyle,
          data: [6714.45, 3819.78, 6074.64, 7327.78, 8037.95, 8038]
        }, {
          name: '累计成交量',
          type: 'line',
          yAxisIndex: 1,
          data: [8.46, 8.69, 9.31, 9.93, 11.25, 12.06]
        }]
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
