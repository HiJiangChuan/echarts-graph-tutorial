<template>
  <div id="myChart" :style="{width: '700px', height: '300px'}"></div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'Welcome to kalacloud.com'
    }
  },
  mounted(){
    this.drawLine();
  },
  methods: {
    drawLine(){
        // 基于刚刚准备好的 DOM 容器，初始化 EChart 实例
        let myChart = this.$echarts.init(document.getElementById('myChart'))
        // 绘制图表
        myChart.setOption({

        backgroundColor: '#EEF1F3',
        color: ["#ee6666", "#91cc75", "#fac858", "#5470c6", "#73c0de", "#3ba272", "#fc8452", "#9a60b4", "#ea7ccc"],
        title: {
            text: "关系图谱",
            textStyle: {
                color: "#000",
                fontWeight: 700,
                fontSize: 20,
                left: "center"
            }
        },
        tooltip: {
            formatter: function(x) {
                return x.data.name;
            },
        },
        legend: [{ //图例
            x: "right",
            show: true,
            data: ["正义的一方", "黑暗的一方"]
        }],
        series: [{
            type: "graph",
            legendHoverLink: true,
            layout: "force",
            categories: [
                { name: "正义的一方", symbolSize: 60 },
                { name: "黑暗的一方", symbolSize: 70 },

            ],
            force: {
                repulsion: [1000, 2000], //节点之间的斥力因子,支持设置成数组表达斥力的范围
                //edgeLength: [10, 20],
                layoutAnimation: true,
                friction: 0.1, //节点的移动速度。取值范围 0 到 1。
               // edgeLength: [70, 90], //两个节点之间的距离，这个距离也会受 repulsion影响
            },
            symbolSize: 60,
            itemStyle: {
                shadowColor: "#666",
                shadowOffsetX: 2,
                shadowOffsetY: 2,
            },
            roam: true, //是否开启鼠标缩放和平移漫游。默认不开启。如果只想要开启缩放或者平移，可以设置成 'scale' 或者 'move'。设置成 true 为都开启
            draggable: true, //节点是否可拖拽，只在使用力引导布局的时候有用。
            edgeSymbol: ["circle", "arrow"],
            edgeSymbolSize: [4, 8],
            cursor: 'pointer',
            label: {
                show: true, // 图形上的文本标签， 可用于说明图形的一些数据信息， 比如值， 名称等
                fontStyle: "oblique",
                // position: "top",
                fontSize: 12,
                color: '#000', //如果设置为 'inherit'，则为视觉映射得到的颜色，如系列色。
                width: 100,
                overflow: "break", //文字超出宽度是否截断或者换行。配置width时有效
            },
            labelLayout: {
                moveOverlap: 'shiftX', //在标签重叠的时候是否挪动标签位置以防止重叠。
                draggable: true, //标签是否可以允许用户通过拖拽二次调整位置。
            },
            emphasis: {
                scale: true, //是否开启高亮后节点的放大效果。
                focus: 'adjacency'
            },
            lineStyle: {
                color: "#666",
                width: 2,
                curveness: 0, //关系线的曲度，支持从 0 到 1 的值，值越大曲度越大。
            },
            edgeLabel: {
                show: true,
                fontWeight: 800,
                fontSize: 12,
                color: "#000",
                formatter: function(x) {
                    return x.data.name
                },
            },
         data: [
          {
            name: "侯亮平",
            des:
              "经过与腐败违法分子的斗争，最终将一批腐败分子送上了审判台，<br/>正义战胜邪恶，自己也迎来了成长。",
            category: "正义的一方",
          },
          {
            name: "李达康",
            des:
              "是一个正义无私的好官。<br/>但为人过于爱惜自己的羽毛，对待身边的亲人和朋友显得有些无情。",
            category: "正义的一方",
          },
          {
            name: "祁同伟",
            des: "汉东省公安厅厅长",
            category: "黑暗的一方",
          },
          {
            name: "陈岩石",
            des:
              "充满正义，平凡而普通的共 产 党人。<br/>对大老虎赵立春，以各种形式执着举报了十二年。<br/>在这场关系党和国家生死存亡的斗争中，老人家以耄耋高龄，<br/>义无反顾地背起了炸 药包，在反腐胜利前夕因病去世。",
            category: "正义的一方",
          },
          {
            name: "陆亦可",
            des: "汉东省检察院反贪局一处处长",
            category: "正义的一方",
          },
          {
            name: "高育良",
            des:
              "年近六十，是一个擅长太极功夫的官场老手。侯亮平、陈海和祁同伟是其学生。",
            category: "黑暗的一方",
          },
          {
            name: "沙瑞金",
            des: "汉东省省委书记",
            category: "正义的一方",
          },
          {
            name: "高小琴",
            des:
              "山水集团董事长，是一位叱咤于政界和商界的风云人物，处事圆滑、精明干练。",
            category: "黑暗的一方",
          },
          {
            name: "高小凤",
            des: "高小琴的双胞胎妹妹。",
            category: "黑暗的一方",
          },
          {
            name: "赵东来",
            des:
              "充满正义，整治恶势力，<br/>在与检察部门的合作中从最初的质疑到之后的通力配合。",
            category: "正义的一方",
          },
          {
            name: "程度",
            des:
              "因犯错误，被李达康书记和赵东来局长点名要清除公安队伍。<br/>但在高小琴的帮助下，祁同伟调他当上了省公安厅办公室副主任。<br/>尽管程度逃避了所有罪责，上面也有人保他，<br/>但最终还是在侯亮平的缜密侦查下被绳之于法。",
            category: "黑暗的一方",
          },
          {
            name: "吴惠芬",
            des: "高育良的妻子，汉东大学明史教授。",
            category: "黑暗的一方",
          },
          {
            name: "赵瑞龙",
            des:
              "副国级人物赵立春的公子哥，官二代，打着老子的旗子，<br/>黑白两道通吃，可谓呼风唤雨，权倾一时。",
            category: "黑暗的一方",
          },
          {
            name: "赵立春",
            des: "副国级领导人，曾经的改革闯将，在权利面前，显得极其渺小。",
            category: "黑暗的一方",
          },
          {
            name: "陈海",
            category: "正义的一方",
          },
          {
            name: "梁璐",
            category: "正义的一方",
          },
          {
            name: "刘新建",
            category: "黑暗的一方",
          },
          {
            name: "欧阳菁",
            category: "黑暗的一方",
          },
          {
            name: "吴心怡",
            category: "正义的一方",
          },
          {
            name: "蔡成功",
            category: "黑暗的一方",
          },
          {
            name: "丁义珍",
            category: "黑暗的一方",
          },
        ],
        link: [
          {
            source: "高育良",
            target: "侯亮平",
            name: "师生",
            des: "侯亮平是高育良的得意门生",
          },
          {
            source: "高育良",
            target: "祁同伟",
            name: "师生",
          },
          {
            source: "赵立春",
            target: "高育良",
            name: "前领导",
          },
          {
            source: "赵立春",
            target: "赵瑞龙",
            name: "父子",
          },
          {
            source: "赵立春",
            target: "刘新建",
            name: "前部队下属",
          },
          {
            source: "李达康",
            target: "赵立春",
            name: "前任秘书",
          },
          {
            source: "祁同伟",
            target: "高小琴",
            name: "情人",
          },
          {
            source: "陈岩石",
            target: "陈海",
            name: "父子",
          },
          {
            source: "陆亦可",
            target: "陈海",
            name: "属下",
          },
          {
            source: "沙瑞金",
            target: "陈岩石",
            name: "故人",
          },
          {
            source: "祁同伟",
            target: "陈海",
            name: "师哥",
          },
          {
            source: "祁同伟",
            target: "侯亮平",
            name: "师哥",
          },
          {
            source: "侯亮平",
            target: "陈海",
            name: "同学，生死朋友",
          },
          {
            source: "高育良",
            target: "吴惠芬",
            name: "夫妻",
          },
          {
            source: "陈海",
            target: "赵东来",
            name: "朋友",
          },
          {
            source: "高小琴",
            target: "高小凤",
            name: "双胞胎",
          },
          {
            source: "赵东来",
            target: "陆亦可",
            name: "爱慕",
          },
          {
            source: "祁同伟",
            target: "程度",
            name: "领导",
          },
          {
            source: "高育良",
            target: "高小凤",
            name: "情人",
          },
          {
            source: "赵瑞龙",
            target: "祁同伟",
            name: "勾结",
          },
          {
            source: "李达康",
            target: "赵东来",
            name: "领导",
          },
          {
            source: "赵瑞龙",
            target: "程度",
            name: "领导",
          },
          {
            source: "沙瑞金",
            target: "李达康",
            name: "领导",
          },
          {
            source: "沙瑞金",
            target: "高育良",
            name: "领导",
          },
          {
            source: "祁同伟",
            target: "梁璐",
            name: "夫妻",
          },
          {
            source: "吴惠芬",
            target: "梁璐",
            name: "朋友",
          },
          {
            source: "李达康",
            target: "欧阳菁",
            name: "夫妻",
          },
          {
            source: "赵瑞龙",
            target: "刘新建",
            name: "洗钱工具",
          },
          {
            source: "赵瑞龙",
            target: "高小琴",
            name: "勾结，腐化",
          },
          {
            source: "赵瑞龙",
            target: "高小凤",
            name: "腐化",
          },
          {
            source: "吴心怡",
            target: "陆亦可",
            name: "母女",
          },
          {
            source: "吴心怡",
            target: "吴惠芬",
            name: "姐妹",
          },
          {
            source: "蔡成功",
            target: "侯亮平",
            name: "发小",
          },
          {
            source: "蔡成功",
            target: "欧阳菁",
            name: "举报",
          },
          {
            source: "欧阳菁",
            target: "刘新建",
            name: "举报",
          },
          {
            source: "刘新建",
            target: "赵瑞龙",
            name: "举报",
          },
          {
            source: "李达康",
            target: "丁义珍",
            name: "领导",
          },
          {
            source: "高小琴",
            target: "丁义珍",
            name: "策划出逃",
          },
          {
            source: "祁同伟",
            target: "丁义珍",
            name: "勾结",
          },
          {
            source: "赵瑞龙",
            target: "丁义珍",
            name: "勾结",
          },
        ],
          },
        ],

    

        });
    }
  }
}
</script>