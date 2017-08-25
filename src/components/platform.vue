<template>
  <div style="position:fixed;top: 80px;width: 100%;height: 100%">
    <div class="chart" id="homeChart" style="width:100%;height:90%;margin-right: -100px"></div>
  </div>
</template>
<script>
  import echarts from 'echarts'
  // import china from "../../static/china.js"
  export default {
    name: 'Home',
    data () {
      return {
        msg: 'oh mygod'
      }
    },
    mounted () {
      var myChart = echarts.init(document.getElementById('homeChart'))
      myChart.setOption({
        title: {
          text: '果树财富业务发布及公比',
          subtext: '单位：万元',
          x: 'center',
          y: '3%',
          textStyle: {
            color: '#fff'
          }
        },
        tooltip: {
          formatter: '{a} <br/>{b} : {c} ({d}%)'
        },
        legend: {
          x: 'center',
          y: '90%',
          data: ['优车贷1月', '优车贷2月', '优车贷3月', '优车贷6月', '优车贷12月', '优车贷18月', '优车贷24月', '优车贷14天']
        },
        toolbox: {
          show: true,
          feature: {
            mark: {show: true},
            dataView: {show: true, readOnly: false},
            magicType: {
              show: true,
              type: ['pie', 'funnel']
            },
            restore: {show: true},
            saveAsImage: {show: true}
          },
          x: '95%',
          y: '5%'
        },
        calculable: true,
        series: [
          {
            name: '1',
            type: 'pie',
            tooltip: false,
            hoverAnimation: false,
            radius: [15, 15.5],
            color: ['#fff'],
            center: ['50%', '50%'],
            labelLine: {
              normal: {
                show: false     // 不需要设置引导线
              }
            },
            data: [
              {value: 0, name: ''}
            ]
          },
          {
            name: '1',
            type: 'pie',
            tooltip: false,
            hoverAnimation: false,
            radius: [220, 222],
            center: ['50%', '50%'],
            color: ['#fff'],
            labelLine: {
              normal: {
                show: false     // 不需要设置引导线
              }
            },
            data: [
               {value: 0, name: ''}
            ]
          },
          {
            name: '面积模式',
            type: 'pie',
            radius: [40, 240],
            center: ['50%', '50%'],
            roseType: 'area',
            data: [
              {value: 883, name: '优车贷14天', ratio: '10.50'},
              {value: 2133, name: '优车贷1月', ratio: '11.20'},
              {value: 631, name: '优车贷2月', ratio: '12.00'},
              {value: 4841, name: '优车贷3月', ratio: '12.50'},
              {value: 1203, name: '优车贷6月', ratio: '13.00'},
              {value: 3788, name: '优车贷12月', ratio: '14.50'},
              {value: 1597, name: '优车贷18月', ratio: '15.50'},
              {value: 286, name: '优车贷24月', ratio: '16.50'}
            ]
          }
        ]
      })
    }

  }
</script>
