```javascript
var sourceData = [{
    name: 'A',
    sales: 142.56,
    services: 64.5
}, {
    name: 'B',
    sales: 471.14,
    services: 76.2
}, {
    name: 'C',
    sales: 42.1,
    services: 34.8
}, {
    name: 'D',
    sales: 63.2,
    services: 97.4
}, {
    name: 'E',
    sales: 97.3,
    services: 67.5
}, {
    name: 'F',
    sales: 782.1,
    services: 37.7
}, {
    name: 'G',
    sales: 41.1,
    services: 12.8
}]

var seriesData = sourceData.map(function(item, index, array) {
    return {
        name: item['name'],
        value: [item['sales'], item['services']]
    }
})

option = {
    xAxis: {
        splitLine: {
            show: false
        },
    },
    yAxis: {
        splitLine: {
            show: false
        },
    },
    visualMap: {
        min: 0,
        max: 800,
        dimension: 0,
        left: 'right',
        top: 'top',
        text: ['高', '低'], // 文本，默认为数值文本
        calculable: true,
        itemWidth: 18,
        itemHeight: 160,
        textStyle: {
            color: '#3259B8',
            height: 56,
            fontSize: 11,
            lineHeight: 60,
        },
        inRange: {
            color: ['#bed6e4', '#0c6797']
        },
        padding: [50, 20],
        orient: 'horizontal',
    },
    series: [{
        symbol: 'rect',
        symbolSize: 40,
        data: seriesData,
        type: 'scatter',
        label: {
            show: true,
            formatter: function(params) {
                if(params && params.name){
                    return params.name;
                }
            }
        },
        markLine: {
            label: {
                normal: {
                    formatter: function(params) {
                        if (params.dataIndex === 0) {
                            return '行业均值:' + params.value;
                        } else if (params.dataIndex === 1) {
                            return '行业均值:' + params.value;
                        }
                        return '行业均值:' + params.value;
                    }
                }
            },
            lineStyle: {
                normal: {
                    color: "#626c91",
                    type: 'solid',
                    width: 1,
                },
                emphasis: {
                    color: "#d9def7"
                }
            },
            data: [{
                xAxis: 420,
                name: '营业额平均线',
                itemStyle: {
                    normal: {
                        color: "#b84a58",
                    }
                }
            }, {
                yAxis: 50,
                name: '服务能力平均线',
                itemStyle: {
                    normal: {
                        color: "#b84a58",
                    }
                }
            }]
        },
    }]
};


```

![效果图](https://github.com/pz25925/Blog/blob/master/%E6%95%88%E6%9E%9C.png)
