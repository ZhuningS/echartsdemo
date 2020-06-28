<template>
  <div class="left_inner">
    <!--隐患统计-->
    <div class="zftz line_hover" style="margin-left: 1vw;margin-top: 1vw">
      <div class="title">•统计折线图1</div>
      <div class="line"></div>
      <div class="yhtj" id="yhtj" style="height: 11vw"></div>
    </div>
    <div class="zftz line_hover" style="margin-left: 1vw;margin-top: 1vw">
      <div class="title">•统计折线图2</div>
      <div class="line"></div>
      <div class="zdls" id="zdls" style="height: 11vw"></div>
    </div>
    <div class="zftz line_hover" style="margin-left: 1vw;margin-top: 1vw">
      <div class="title">•统计折线图3</div>
      <div class="line"></div>
      <div class="_3section" id="_3section" style="height: 11vw"></div>
    </div>
    <div class="zftz line_hover" style="margin-left: 1vw;margin-top: 1vw">
      <div class="title">•统计折线图4</div>
      <div class="line"></div>
      <div class="_5section" id="_5section" style="height: 11vw"></div>
    </div>
  </div>
</template>
<script>
  export default {
    props: ['msg'],
    data() {
      return {
        left: {
          yhtj: {
            xdata: ['201907', '201908', '201909', '201910', '201911','201912'],
            ydata1: [27.2, 25.9, 25.9, 25.3, 28.1,24.6],
            ydata2: [31, 37, 37, 46, 37, 45],
            ydata3: [757, 763, 762, 754, 755, 756]
          },
          zdls:{
            xdata: [],
            ydata1: [],
            ydata2: []
          },
          _3section:{
            xdata: [],
            ydata1: [],
            ydata2: [],
            ydata3: [],
            ydata4: [],
            ydata5: [],
            ydata6: []
          },
          _5section:{
            xdata: [],
            ydata1: [],
            ydata2: [],
            ydata3: [],
            ydata4: [],
            ydata5: [],
            ydata6: [],
            ydata7: [],
            ydata8: [],
            ydata9: [],
            ydata10: []
          },
        }
      }
    },
    methods: {
      // 隐患统计示例
      loadYhtj() {
        let myChart = this.$echarts.init(document.getElementById('yhtj'));
        let option = {
          tooltip: {
            trigger: 'axis'
          },
          legend: {
            bottom: -6,
            textStyle: {
              color: '#5A7898'
            },
            width: 300,
            data: ['环境温度[℃]', '环境湿度[%]', '大气压力[mmHg]', '来源']
          },
          grid: {
            top: 8,
            left: '30%',
            // width: '1000px',
            right: '30%',
            bottom: 24,
            containLabel: true
          },
          xAxis: {
            type: 'category',
            interval: 3,
            boundaryGap: false,
            axisTick: {
              show: false
            },
            axisLine: {
              lineStyle: {
                color: "#87ACE9"
              }
            },
            axisTick:{interval:0},
            axisLabel:{interval:0},
            data: this.left.yhtj.xdata
          },
          yAxis: [
            {
            type: 'value',
            axisTick: {
              show: false
            },
            splitLine: {
              show: false
            },
            axisLine: {
              lineStyle: {
                color: "#87ACE9"
              }
            }
          },
          {
            type: 'value',
            axisTick: {
              show: false
            },
            splitLine: {
              show: false
            },
            axisLine: {
              lineStyle: {
                color: "#570A3E"
              }
            }
          }
          ],
          series: [
            {
              name: '环境温度[℃]',
              type: 'line',
              color: ['#060B6A'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left.yhtj.ydata1,
              yAxisIndex:0
            },
            {
              name: '环境湿度[%]',
              type: 'line',
              color: ['#266611'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left.yhtj.ydata2,
              yAxisIndex:0
            },
            {
              name: '大气压力[mmHg]',
              type: 'line',
              color: ['#570A3E'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left.yhtj.ydata3,
              yAxisIndex:1
            }
            // {
            //   name: '来源',
            //   type: 'line',
            //   color: ['#5A6016'],
            //   symbol: 'circle',
            //   symbolSize: 10,
            //   data: this.left.yhtj.jtgl
            // },
            // {
            //   name: '城管执法',
            //   type: 'line',
            //   color: ['#065F65'],
            //   symbol: 'circle',
            //   symbolSize: 10,
            //   data: this.left.yhtj.cgzf
            // },
            // {
            //   name: '市场管理',
            //   type: 'line',
            //   color: ['#A726B0'],
            //   symbol: 'circle',
            //   symbolSize: 10,
            //   data: this.left.yhtj.scjg
            // }
          ]
        };
        myChart.setOption(option);
      },
      loadzdls() {
        let myChart = this.$echarts.init(document.getElementById('zdls'));
        let option = {
          tooltip: {
            trigger: 'axis'
          },
          legend: {
            bottom: -6,
            textStyle: {
              color: '#5A7898'
            },
            width: 300,
            data: ['高速段[%]', '低速段[L/s]']
          },
          grid: {
            top: 8,
            left: '30%',
            // width: '1000px',
            right: '30%',
            bottom: 24,
            containLabel: true
          },
          xAxis: {
            type: 'category',
            interval: 3,
            boundaryGap: false,
            axisTick: {
              show: false
            },
            axisLine: {
              lineStyle: {
                color: "#87ACE9"
              }
            },
            axisTick:{interval:0},
            axisLabel:{interval:0},
            data: this.left.zdls.xdata
          },
          yAxis: [
            {
            type: 'value',
            axisTick: {
              show: false
            },
            splitLine: {
              show: false
            },
            axisLine: {
              lineStyle: {
                color: "#87ACE9"
              }
            }
          },
          {
            type: 'value',
            axisTick: {
              show: false
            },
            splitLine: {
              show: false
            },
            axisLine: {
              lineStyle: {
                color: "#570A3E"
              }
            }
          }
          ],
          series: [
            {
              name: '高速段[%]',
              type: 'line',
              color: ['#060B6A'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left.zdls.ydata1,
              yAxisIndex:0
            },
            {
              name: '低速段[L/s]',
              type: 'line',
              color: ['#266611'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left.zdls.ydata2,
              yAxisIndex:1
            }
          ]
        };
        myChart.setOption(option);
      },
      load_3section() {
        let myChart = this.$echarts.init(document.getElementById('_3section'));
        let option = {
          tooltip: {
            trigger: 'axis'
          },
          legend: {
            bottom: -6,
            textStyle: {
              color: '#5A7898'
            },
            width: 300,
            data: ['呼气低速段[%]', '呼气中速段[%]', '呼气高速段[%]', '吸气低速段[%]', '吸气中速段[%]', '吸气高速段[%]']
          },
          grid: {
            top: 8,
            left: '30%',
            // width: '1000px',
            right: '30%',
            bottom: 24,
            containLabel: true
          },
          xAxis: {
            type: 'category',
            interval: 3,
            boundaryGap: false,
            axisTick: {
              show: false
            },
            axisLine: {
              lineStyle: {
                color: "#87ACE9"
              }
            },
            axisTick:{interval:0},
            axisLabel:{interval:0},
            data: this.left._3section.xdata
          },
          yAxis: [
            {
            type: 'value',
            axisTick: {
              show: false
            },
            splitLine: {
              show: false
            },
            axisLine: {
              lineStyle: {
                color: "#87ACE9"
              }
            }
          }
          ],
          series: [
            {
              name: '呼气低速段[%]',
              type: 'line',
              color: ['#060B6A'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._3section.ydata1
            },
            {
              name: '呼气中速段[%]',
              type: 'line',
              color: ['#266611'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._3section.ydata2
            },
            {
              name: '呼气高速段[%]',
              type: 'line',
              color: ['#570A3E'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._3section.ydata3
            },
            {
              name: '吸气低速段[%]',
              type: 'line',
              color: ['#5A6016'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._3section.ydata4
            },
            {
              name: '吸气中速段[%]',
              type: 'line',
              color: ['#065F65'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._3section.ydata5
            },
            {
              name: '吸气高速段[%]',
              type: 'line',
              color: ['#A726B0'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._3section.ydata6
            }
          ]
        };
        myChart.setOption(option);
      },
      load_5section() {
        let myChart = this.$echarts.init(document.getElementById('_5section'));
        let option = {
          tooltip: {
            trigger: 'axis'
          },
          legend: {
            bottom: -6,
            textStyle: {
              color: '#5A7898'
            },
            width: 300,
            data: ['呼1段[%]', '呼2段[%]', '呼3段[%]', '呼4段[%]', '呼5段[%]', '吸1段[%]', '吸2段[%]', '吸3段[%]', '吸4段[%]', '吸5段[%]']
          },
          grid: {
            top: 8,
            left: '30%',
            // width: '1000px',
            right: '30%',
            bottom: 24,
            containLabel: true
          },
          xAxis: {
            type: 'category',
            interval: 3,
            boundaryGap: false,
            axisTick: {
              show: false
            },
            axisLine: {
              lineStyle: {
                color: "#87ACE9"
              }
            },
            axisTick:{interval:0},
            axisLabel:{interval:0},
            data: this.left._5section.xdata
          },
          yAxis: [
            {
            type: 'value',
            axisTick: {
              show: false
            },
            splitLine: {
              show: false
            },
            axisLine: {
              lineStyle: {
                color: "#87ACE9"
              }
            }
          }
          ],
          series: [
            {
              name: '呼1段[%]',
              type: 'line',
              color: ['#060B6A'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._5section.ydata1
            },
            {
              name: '呼2段[%]',
              type: 'line',
              color: ['#266611'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._5section.ydata2
            },
            {
              name: '呼3段[%]',
              type: 'line',
              color: ['#570A3E'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._5section.ydata3
            },
            {
              name: '呼4段[%]',
              type: 'line',
              color: ['#5A6016'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._5section.ydata4
            },
            {
              name: '呼5段[%]',
              type: 'line',
              color: ['#065F65'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._5section.ydata5
            },
            {
              name: '吸1段[%]',
              type: 'line',
              color: ['#A726B0'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._5section.ydata6
            },
            {
              name: '吸2段[%]',
              type: 'line',
              color: ['#A726B0'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._5section.ydata7
            },
            {
              name: '吸3段[%]',
              type: 'line',
              color: ['#A726B0'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._5section.ydata8
            },
            {
              name: '吸4段[%]',
              type: 'line',
              color: ['#A726B0'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._5section.ydata9
            },
            {
              name: '吸5段[%]',
              type: 'line',
              color: ['#A726B0'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left._5section.ydata10
            }
          ]
        };
        myChart.setOption(option);
      },
    },
    created() {
      this.$nextTick(function () {
        this.loadYhtj();
        this.loadZdls();
        this.load_3section();
        this.load_5section();
      });
    }
  }
</script>