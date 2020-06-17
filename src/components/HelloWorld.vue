<template>
  <div class="left_inner">
    <!--全员上报-->
    <div class="zftz line_hover" style="margin-left: 1vw;margin-top: 1vw">
      <div class="title">•全员上报</div>
      <div class="line"></div>
      <div class="qysb" id="qysb" style="height: 11vw"></div>
    </div>
    <!--隐患统计-->
    <div class="zftz line_hover" style="margin-left: 1vw;margin-top: 1vw">
      <div class="title">•隐患统计</div>
      <div class="line"></div>
      <div class="yhtj" id="yhtj" style="height: 11vw"></div>
    </div>
  </div>
</template>
<script>
  export default {
    props: ['msg'],
    data() {
      return {
        left: {
          qysb: {
            finish: [30, 45, 30, 45, 30, 36],
            unFinish: [70, 55, 70, 55, 70, 64]
          },
          yhtj: {
            xdata: ['201907', '201908', '201909', '201910', '201911'],
            zhxf: [225, 150, 50, 60, 120],
            hjws: [120, 40, 40, 30, 90],
            yjbz: [70, 80, 90, 40, 120],
            jtgl: [40, 50, 30, 40, 180],
            cgzf: [10, 20, 10, 20, 70],
            scjg: [15, 120, 90, 60, 25]
          }
        }
      }
    },
    methods: {
      // 全员上报示例
      loadQysb() {
        // 基于准备好的dom，初始化echarts实例
        let myChart = this.$echarts.init(document.getElementById('qysb'));
        // 指定图表的配置项和数据
        let option = {
          grid: {     //直角坐标系内绘图网格
            top: 8,     //grid组件离容器上侧的距离
            left: 80,
            bottom: 24
          },
          // title: {text: '供应商产品质量'},    标题(包括主标题和副标题)
          tooltip: {         //提示框组件
            show: true,      //是否显示提示框组件
            trigger: 'item'      //触发方式
          },
          legend: {        //图例组件(标记)
            bottom: -6,      //图例组件离容器下侧的距离
            itemWidth: 14,    //图例标记的图形宽度
            textStyle: {     //图例的公用文本样式
              color: '#5A7898'
            },
            data: ['处理完成', '处理未完成']    //图例的数据数组
          },
          xAxis: {      //直角坐标系 grid 中的 x 轴
            // data: [],
            // type: 'value',
            show: false
          },
          yAxis: {       //直角坐标系 grid 中的 y 轴
            type: 'category',       //坐标轴类型
            data: ['智慧消防', '环境卫生', '应急保障', '交通管理', '城管执法', '市场管理'],     //类目数据
            axisLabel: {       //坐标轴刻度标签的相关设置
              color: '#5A7898'
            },
            axisTick: {     //坐标轴刻度相关设置
              show: false
            }
          },
          series: [{    //系列列表,每个系列通过 type 决定自己的图表类型
            type: 'bar',
            name: '处理完成',
            data: this.left.qysb.finish,
            stack: '柱子',
            // barWidth: '20%',
            barMaxWidth: '30',    //柱条的最大宽度
            color: '#0A626F',
            itemStyle: {       //图形样式
              barBorderRadius: [8, 0, 0, 8]
            },
            label: {     //图形上的文本标签
              normal: {
                color: "#81ABD2",
                show: true,
                position: 'inside',
                formatter: function (obj) {
                  return obj.value;
                }
              }
            }
          }, {
            type: 'bar',
            name: '处理未完成',
            data: this.left.qysb.unFinish,
            stack: '柱子',
            // barWidth: '20%',
            barMaxWidth: '30',
            color: '#903C3C',
            itemStyle: {
              barBorderRadius: [0, 8, 8, 0]
            },
            label: {
              normal: {
                color: "#DB919B",
                show: true,
                position: 'inside',
                formatter: function (obj) {
                  return obj.value;
                }
              }
            }
          }
          ]
        };
        // 使用刚指定的配置项和数据显示图表
        myChart.setOption(option);
      },
      // 隐患统计示例
      loadYhtj() {
        let myChart = this.$echarts.init(document.getElementById('yhtj'));
        let option = {
          tooltip: {
            trigger: 'axis'
          },
          legend: {
            bottom: 0,
            textStyle: {
              color: '#5A7898'
            },
            width: 300,
            data: ['智慧消防', '环境卫生', '应急保障', '交通管理', '城管执法', '市场管理']
          },
          grid: {
            top: 10,
            left: '0',
            right: '8%',
            bottom: '50',
            containLabel: true
          },
          xAxis: {
            type: 'category',
            boundaryGap: false,
            axisTick: {
              show: false
            },
            axisLine: {
              lineStyle: {
                color: "#87ACE9"
              }
            },
            data: this.left.yhtj.xdata
          },
          yAxis: {
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
          series: [
            {
              name: '智慧消防',
              type: 'line',
              color: ['#060B6A'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left.yhtj.zhxf
            },
            {
              name: '环境卫生',
              type: 'line',
              color: ['#266611'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left.yhtj.hjws
            },
            {
              name: '应急保障',
              type: 'line',
              color: ['#570A3E'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left.yhtj.yjbz
            },
            {
              name: '交通管理',
              type: 'line',
              color: ['#5A6016'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left.yhtj.jtgl
            },
            {
              name: '城管执法',
              type: 'line',
              color: ['#065F65'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left.yhtj.cgzf
            },
            {
              name: '市场管理',
              type: 'line',
              color: ['#A726B0'],
              symbol: 'circle',
              symbolSize: 10,
              data: this.left.yhtj.scjg
            }
          ]
        };
        myChart.setOption(option);
      }
    },
    created() {
      this.$nextTick(function () {
        this.loadQysb();
        this.loadYhtj();
      });
    }
  }
</script>