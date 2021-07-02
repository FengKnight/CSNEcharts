<template>
    <div>
        <el-button>饼图</el-button>
        <el-button>折线图</el-button>
        <el-button @click="changZoom">坐标轴</el-button>
        <el-button @click="changEchar">detaset</el-button>

        <el-row>
            <el-col :span="8">
                <div id="e_pipe" style="width:500px; height:400px;"></div>
            </el-col>
            <el-col :span="8">
                <div id="e_bar" style="width:500px; height:400px;"></div>
            </el-col>
            <el-col :span="8">
                <div id="e_zoom" style="width:500px; height:400px;"></div>
            </el-col>
        </el-row>
    </div>

</template>

<script>
    import echarts from "echarts";

    export default {
        name: "pipe",
        data(){
            return{
                e_pipe:null,
            }
        },
        methods:{
            changZoom(){
                var data1 = [];
                var data2 = [];
                var data3 = [];

                var random = function (max) {
                    return (Math.random() * max).toFixed(3);
                };

                for (var i = 0; i < 500; i++) {
                    data1.push([random(15), random(10), random(1)]);
                    data2.push([random(10), random(10), random(1)]);
                    data3.push([random(15), random(10), random(1)]);
                }

                this.e_zoom = echarts.init(document.getElementById('e_zoom'));
                this.e_zoom.setOption({
                    animation: false,
                    legend: {
                        data: ['scatter', 'scatter2', 'scatter3']
                    },
                    tooltip: {
                    },
                    xAxis: {
                        type: 'value',
                        min: 'dataMin',
                        max: 'dataMax',
                        splitLine: {
                            show: true
                        }
                    },
                    yAxis: {
                        type: 'value',
                        min: 'dataMin',
                        max: 'dataMax',
                        splitLine: {
                            show: true
                        }
                    },
                    dataZoom: [
                        {
                            type: 'slider',
                            show: true,
                            xAxisIndex: [0],
                            start: 1,
                            end: 35
                        },
                        {
                            type: 'slider',
                            show: true,
                            yAxisIndex: [0],
                            left: '93%',
                            start: 29,
                            end: 36
                        },
                        {
                            type: 'inside',
                            xAxisIndex: [0],
                            start: 1,
                            end: 35
                        },
                        {
                            type: 'inside',
                            yAxisIndex: [0],
                            start: 29,
                            end: 36
                        }
                    ],
                    series: [
                        {
                            name: 'scatter',
                            type: 'scatter',
                            itemStyle: {
                                normal: {
                                    opacity: 0.8
                                }
                            },
                            symbolSize: function (val) {
                                return val[2] * 40;
                            },
                            data: data1
                        },
                        {
                            name: 'scatter2',
                            type: 'scatter',
                            itemStyle: {
                                normal: {
                                    opacity: 0.8
                                }
                            },
                            symbolSize: function (val) {
                                return val[2] * 40;
                            },
                            data: data2
                        },
                        {
                            name: 'scatter3',
                            type: 'scatter',
                            itemStyle: {
                                normal: {
                                    opacity: 0.8,
                                }
                            },
                            symbolSize: function (val) {
                                return val[2] * 40;
                            },
                            data: data3
                        }
                    ]
                })
            },
            changEchar(){
                this.e_bar = echarts.init(document.getElementById('e_bar'));
                this.e_bar.setOption({
                    legend: {},
                    tooltip: {
                        trigger: 'axis',
                        showContent: false
                    },
                    dataset: {
                        source: [
                            ['product', '2012', '2013', '2014', '2015', '2016', '2017'],
                            ['Milk Tea', 56.5, 82.1, 88.7, 70.1, 53.4, 85.1],
                            ['Matcha Latte', 51.1, 51.4, 55.1, 53.3, 73.8, 68.7],
                            ['Cheese Cocoa', 40.1, 62.2, 69.5, 36.4, 45.2, 32.5],
                            ['Walnut Brownie', 25.2, 37.1, 41.2, 18, 33.9, 49.1]
                        ]
                    },
                    xAxis: {type: 'category'},
                    yAxis: {gridIndex: 0},
                    grid: {top: '55%'},
                    series: [
                        {type: 'line', smooth: true, seriesLayoutBy: 'row', emphasis: {focus: 'series'}},
                        {type: 'line', smooth: true, seriesLayoutBy: 'row', emphasis: {focus: 'series'}},
                        {type: 'line', smooth: true, seriesLayoutBy: 'row', emphasis: {focus: 'series'}},
                        {type: 'line', smooth: true, seriesLayoutBy: 'row', emphasis: {focus: 'series'}},
                        {
                            type: 'pie',
                            id: 'pie',
                            radius: '30%',
                            center: ['50%', '25%'],
                            emphasis: {focus: 'data'},
                            label: {
                                formatter: '{b}: {@2012} ({d}%)'
                            },
                            encode: {
                                itemName: 'product',
                                value: '2012',
                                tooltip: '2012'
                            }
                        }
                    ]
                })

            },
            draw(){
                this.e_pipe = echarts.init(document.getElementById('e_pipe'));
                this.e_pipe.setOption( {
                    title: {
                        x: 'center',                 // 水平安放位置，默认为左对齐，可选为：
                                                   // 'center' ¦ 'left' ¦ 'right'
                                                   // ¦ {number}（x坐标，单位px）
                        y: 'top',                  // 垂直安放位置，默认为全图顶端，可选为：
                                                   // 'top' ¦ 'bottom' ¦ 'center'
                                                   // ¦ {number}（y坐标，单位px）
                        //textAlign: null          // 水平对齐方式，默认根据x设置自动调整
                        backgroundColor: 'rgba(0,0,0,0)',
                        borderColor: '#54bbab',       // 标题边框颜色
                        borderWidth: 1,            // 标题边框线宽，单位px，默认为0（无边框）
                        padding: 5,                // 标题内边距，单位px，默认各方向内边距为5，
                                                   // 接受数组分别设定上右下左边距，同css
                        itemGap: 10,               // 主副标题纵向间隔，单位px，默认为10，
                        textStyle: {
                            fontSize: 18,
                            fontWeight: 'bolder',
                            color: '#86e4f5', // 主标题文字颜色
                        },
                        text:'这是一个饼图', //主标题
                        subtext:'自定义系列',//副标题
                        subtextStyle: {
                            color: '#83b4c7'          // 副标题文字颜色
                        }
                    },

                    legend: {//图例左上角位置处
                        type:'scroll',//设置图例过多时候翻页处理
                        pageIconColor:'#fff',
                        pageButtonPosition:'start',
                        //orient: 'vertical',      // 布局方式，默认为水平布局，可选为：
                                                   // 'horizontal' ¦ 'vertical'
                        x: 'left',               // 水平安放位置，默认为全图居中，可选为：
                                                   // 'center' ¦ 'left' ¦ 'right'
                                                   // ¦ {number}（x坐标，单位px）
                        y: 'bottom',                  // 垂直安放位置，默认为全图顶端，可选为：
                                                   // 'top' ¦ 'bottom' ¦ 'center'
                                                   // ¦ {number}（y坐标，单位px）
                        backgroundColor: 'rgba(0,0,0,0)',
                        borderColor: '#ccc',       // 图例边框颜色
                        borderWidth: 0,            // 图例边框线宽，单位px，默认为0（无边框）
                        padding: 5,                // 图例内边距，单位px，默认各方向内边距为5，
                                                   // 接受数组分别设定上右下左边距，同css
                        itemGap: 50,               // 各个item之间的间隔，单位px，默认为10，
                                                   // 横向布局时为水平间隔，纵向布局时为纵向间隔
                        itemWidth: 20,             // 图例图形宽度
                        itemHeight: 14,            // 图例图形高度
                        textStyle: {
                            color: '#ffffff'          // 图例文字颜色
                        }
                    },
                    tooltip: {                      //放在对应框上的提示
                        trigger: 'item',           // 触发类型，默认数据触发，见下图，可选为：'item' ¦ 'axis'
                        showDelay: 20,             // 显示延迟，添加显示延迟可以避免频繁切换，单位ms
                        hideDelay: 100,            // 隐藏延迟，单位ms
                        transitionDuration : 0.4,  // 动画变换时间，单位s
                        backgroundColor: 'rgba(0,0,0,0.7)',     // 提示背景颜色，默认为透明度为0.7的黑色
                        borderColor: '#333',       // 提示边框颜色
                        borderRadius: 4,           // 提示边框圆角，单位px，默认为4
                        borderWidth: 0,            // 提示边框线宽，单位px，默认为0（无边框）
                        padding: 5,                // 提示内边距，单位px，默认各方向内边距为5，
                                                   // 接受数组分别设定上右下左边距，同css
                        axisPointer : {            // 坐标轴指示器，坐标轴触发有效
                            type : 'line',         // 默认为直线，可选为：'line' | 'shadow'
                            lineStyle : {          // 直线指示器样式设置
                                color: '#48b',
                                width: 2,
                                type: 'solid'
                            },
                            shadowStyle : {                       // 阴影指示器样式设置
                                width: 'auto',                   // 阴影大小
                                color: 'rgba(150,150,150,0.3)'  // 阴影颜色
                            }
                        },
                        textStyle: {
                            color: '#fff'
                        }
                    },



                    backgroundColor: '#2c343c',
                    visualMap: {
                        show: false,
                        min: 80,
                        max: 800,
                        inRange: {
                            colorLightness: [0, 1]
                        }
                    },
                    series : [
                        {
                            name: '访问来源',
                            type: 'pie',
                            radius: '55%',
                            data:[
                                {value:235, name:'视频广告'},
                                {value:274, name:'联盟广告'},
                                {value:310, name:'邮件营销'},
                                {value:335, name:'直接访问'},
                                {value:400, name:'搜索引擎'}
                            ],
                            roseType: 'angle',
                            label: {
                                normal: {
                                    textStyle: {
                                        color: 'rgba(255, 255, 255, 0.3)'
                                    }
                                }
                            },
                            labelLine: {
                                normal: {
                                    lineStyle: {
                                        color: 'rgba(255, 255, 255, 0.3)'
                                    }
                                }
                            },
                            itemStyle: {
                                normal: {
                                    color: '#c23531',
                                    shadowBlur: 200,
                                    shadowColor: 'rgba(0, 0, 0, 0.5)'
                                }
                            }
                        }
                    ]
                })
            }
        },
        mounted: function () {
            this.draw()
        },

    }
</script>

<style scoped>

</style>