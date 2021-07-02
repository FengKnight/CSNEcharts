
<template>
    <div class="chart-container">
        <el-row >
            <el-col :span="12">
                <div id="litiyuanzhu" style="width:500px; height:400px;"></div>
            </el-col>
        </el-row>
    </div>
</template>

<script>
    import echarts from 'echarts'
    import  'echarts-liquidfill'

    export default {
        data() {
            return {
                litiyuanzhu: null,
            }
        },

        methods: {
            drawColumnChart() {
                this.litiyuanzhu = echarts.init(document.getElementById('litiyuanzhu'));
                let xData = ["本年话务总量", "本年人工话务量", "每万客户呼入量"];
                let yData = [0, 1230, 425];
                this.litiyuanzhu.setOption({
                    backgroundColor: '#061326',
                    "grid": {
                        "top": "25%",
                        "left": "-5%",
                        "bottom": "5%",
                        "right": "5%",
                        "containLabel": true
                    },
                    tooltip:{
                        show:true
                    },
                    animation: false,
                    "xAxis": [{
                        "type": "category",
                        "data": xData,
                        "axisTick": {
                            "alignWithLabel": true
                        },
                        "nameTextStyle": {
                            "color": "#82b0ec"
                        },
                        "axisLine": {
                            show: false,
                            "lineStyle": {
                                "color": "#82b0ec"
                            }
                        },
                        "axisLabel": {
                            "textStyle": {
                                "color": "#fff"
                            },
                            margin: 30
                        }
                    }],
                    "yAxis": [{
                        show: false,
                        "type": "value",
                        "axisLabel": {
                            "textStyle": {
                                "color": "#fff"
                            },
                        },
                        "splitLine": {
                            "lineStyle": {
                                "color": "#0c2c5a"
                            }
                        },
                        "axisLine": {
                            "show": false
                        }
                    }],
                    "series": [{
                        "name": "",
                        type: 'pictorialBar',
                        barMinHeight:0.1,
                        symbolSize: [40, 10],
                        symbolOffset: [0, -6],
                        symbolPosition: 'end',
                        z: 12,
                        // "barWidth": "0",
                        "label": {
                            "normal": {
                                "show": true,
                                "position": "top",
                                // "formatter": "{c}%"
                                fontSize: 15,
                                fontWeight: 'bold',
                                color: '#34DCFF'
                            }
                        },
                        color: "#2DB1EF",
                        data: yData
                    },
                        {
                            name: '',
                            barMinHeight:1,
                            type: 'pictorialBar',
                            symbolSize: [40, 10],
                            symbolOffset: [0, 7],
                            // "barWidth": "20",
                            z: 12,
                            "color": "#2DB1EF",
                            "data": yData
                        },
                        {
                            name: '',
                            barMinHeight:0.1,
                            type: 'pictorialBar',
                            symbolSize: [50, 15],
                            symbolOffset: [0, 12],
                            z: 10,
                            itemStyle: {
                                normal: {
                                    color: 'transparent',
                                    borderColor: '#2EA9E5',
                                    borderType: 'solid',
                                    borderWidth: 1
                                }
                            },
                            data: yData
                        },
                        {
                            name: '',
                            barMinHeight:0.1,
                            type: 'pictorialBar',
                            symbolSize: [70, 20],
                            symbolOffset: [0, 18],
                            z: 10,
                            itemStyle: {
                                normal: {
                                    color: 'transparent',
                                    borderColor: '#19465D',
                                    borderType: 'solid',
                                    borderWidth: 2
                                }
                            },
                            data: yData
                        },
                        {
                            type: 'bar',
                            barMinHeight:0.1,
                            //silent: true,
                            "barWidth": "40",
                            barGap: '10%', // Make series be overlap

                            barCateGoryGap: '10%',
                            itemStyle: {
                                normal: {
                                    color: new echarts.graphic.LinearGradient(0, 0, 0, 0.7, [{
                                        offset: 0,
                                        color: "#38B2E6"
                                    },
                                        {
                                            offset: 1,
                                            color: "#0B3147"
                                        }
                                    ]),
                                    opacity: .8
                                },
                            },
                            data: yData
                        }
                    ]
                });
            },

            drawCharts() {
                this.drawColumnChart()

            },
        },

        mounted: function () {
            this.drawCharts()
        },
        updated: function () {
            this.drawCharts()
        }
    }
</script>

<style scoped>
    .chart-container {
        background-color:white;
        height: 100%;
        width: 50%;
    }

    .el-col {
        padding: 30px;
    }
</style>
