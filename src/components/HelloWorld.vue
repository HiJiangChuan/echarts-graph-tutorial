<template>
  <div id="myChart" :style="{width: '1000px', height: '700px'}"></div>
</template>

<script>
export default {
  mounted(){
    this.drawLine();
  },
  methods: {
    drawLine(){
        // 基于刚刚准备好的 DOM 容器，初始化 EChart 实例
        let myChart = this.$echarts.init(document.getElementById('myChart'))
        // 绘制图表
        myChart.setOption({
backgroundColor: '#f6f5f3',
  color: [
    '#02c9c9',
    '#bccf3d',
    '#ffc300'
  ],
  title: { 
    text: '西游记人物关系图 - 卡拉云',
    textStyle: {
      color: '#368cbf',
      fontWeight: 700,
      fontSize: 30,
      left: 'center'
    }
  }, // 标题及标题颜色、尺寸、位置
    legend: [ // 增加图示标签，我们可以点击图示隐藏相关节点
    {
      x: 'right',
      show: true,
      data: ['西天取经团队', '佛法家族', '道法家族']
    }],
  series: [
    {
      type: 'graph', // 类型设置为关系图
      legendHoverLink: true,  // 可以点击图例来隐藏一个组
      layout: 'force',
      categories: [
        { name: '西天取经团队', symbolSize: 60 },
        { name: '佛法家族', symbolSize: 60 },
        { name: '道法家族', symbolSize: 60 }
      ],
      force: {
        repulsion: [1000, 1200], //每个节点之间的斥力因子，越大离的越远
        layoutAnimation: true,
        friction: 0.3, //刷新时节点的移动速度，越大越快，0 - 1 之间
        edgeLength: [100, 130] //两节点之间的距离
      },
  
      label: {
        show: true, // 节点圆盘上的文字
        fontStyle: 'italic', //文字风格，normal，italic，oblique 三种可选
        fontSize: 12,
        color: '#000000',
      },

      symbolSize: 60, //全局节点尺寸
      itemStyle: {  // 给节点加上阴影，显着立体
        shadowColor: '#C0C0C0', 
        shadowOffsetX: 2,
        shadowOffsetY: 2
      },
        //让节点可以通过鼠标拖拽和移动的设置
      roam: true, //开启鼠标平移及缩放
      draggable: true, //节点是否支持鼠标拖拽。
      edgeSymbol: ['circle', 'arrow'],//两节点连线的样式
      edgeSymbolSize: [5, 10],
      cursor: 'pointer', //鼠标悬浮时在图形元素上时鼠标的样式

      labelLayout: {
        moveOverlap: 'shiftX', //标签重叠时，挪动标签防止重叠
        draggable: true //节点标签是否允许鼠标拖拽定位
      },
      emphasis: {
        scale: true, //节点放大效果
        focus: 'adjacency'
      },
      lineStyle: {
        color: '#3d3d3f',
        width: 2,
        curveness: 0 //节点连线的曲率，0-1 越大越弯。
      },
      
      data: [
        {
          name: '玄奘',
          symbolSize: 80,
          category: '西天取经团队'
        },
        {
          name: '孙悟空',
          category: '西天取经团队'
        },
        {
          name: '猪八戒',
          category: '西天取经团队'
        },
        {
          name: '沙僧',
          category: '西天取经团队'
        },
        {
          name: '白龙马',
          category: '西天取经团队'
        },
        {
          name: '如来佛祖',
          symbolSize: 80,
          category: '佛法家族'
        },
        {
          name: '观世音菩萨',
          category: '佛法家族'
        },
        {
          name: '菩提祖师',
          category: '佛法家族'
        },
        {
          name: '文殊菩萨',
          category: '佛法家族'
        },
        {
          name: '弥勒佛',
          category: '佛法家族'
        },
        {
          name: '玉皇大帝',
          symbolSize: 80,
          category: '道法家族'
        },
        {
          name: '太上老君',
          category: '道法家族'
        },
        {
          name: '托塔天王',
          category: '道法家族'
        },
        {
          name: '王母娘娘',
          category: '道法家族'
        },
        {
          name: '龙王',
          category: '道法家族'
        },
        {
          name: '哪吒',
          category: '道法家族'
        }
      ],
      links: [
        {
          source: '玄奘',
          target: '孙悟空'
        },
        {
          source: '玄奘',
          target: '猪八戒'
        },
        {
          source: '玄奘',
          target: '沙僧'
        },
        {
          source: '玄奘',
          target: '白龙马'
        },
        {
          source: '如来佛祖',
          target: '文殊菩萨'
        },
        {
          source: '如来佛祖',
          target: '菩提祖师'
        },
        {
          source: '如来佛祖',
          target: '弥勒佛'
        },
        {
          source: '如来佛祖',
          target: '观世音菩萨'
        },
         {
          source: '如来佛祖',
          target: '孙悟空'
        },
         {
          source: '观世音菩萨',
          target: '孙悟空'
        },
                {
          source: '太上老君',
          target: '孙悟空'
        },
                     {
          source: '龙王',
          target: '孙悟空'
        },
                       {
          source: '龙王',
          target: '玄奘'
        },               {
          source: '弥勒佛',
          target: '玄奘'
        },
    {
        source: '菩提祖师',
          target: '玄奘'
        },
                       {
          source: '龙王',
          target: '白龙马'
        },
        {
          source: '玉皇大帝',
          target: '王母娘娘'
        },
        {
                  source: '玉皇大帝',
          target: '玄奘'
        },
        {
          source: '托塔天王',
          target: '哪吒'
        },
        {
          source: '玉皇大帝',
          target: '太上老君'
        },
        {
          source: '玉皇大帝',
          target: '托塔天王'
        },
        {
          source: '玉皇大帝',
          target: '龙王'
        },
        {
          source: '孙悟空',
          target: '哪吒'
        },
        {
          source: '如来佛祖',
          target: '玉皇大帝'
        },
        {
          source: '王母娘娘',
          target: '孙悟空'
        },
        {
          source: '观世音菩萨',
          target: '孙悟空'
        },
        {
          source: '观世音菩萨',
          target: '玄奘'
        },
        {
          source: '玉皇大帝',
          target: '孙悟空'
        },
        {
          source: '如来佛祖',
          target: '玄奘'
        }
      ]
    }
  ]


        

        });
    }
  }
}
</script>