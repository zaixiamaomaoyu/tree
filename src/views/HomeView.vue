<template>
  <div class="home">
    <el-tree
      :data='data'
      :props='defaultProps'
      @node-click="handleNodeClick"
      show-checkbox
      node-key='id'
      :default-expanded-keys='[2]'
      :default-checked-keys='[3]'
      :highlight-current='true'
      default-expand-all
      draggable
      @node-drag-start='start'
      @node-drag-enter='enter'
    ></el-tree>
    <div
      class="box"
      ref='box'
    ></div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    // HelloWorld
  },
  data () {
    return {
      data: [
        {
          id: 1,
          label: '学校',
          children: [{
            id: 3,
            label: '学院',
            children: [{
              id: 5,
              label: '班级',
              children: [{
                id: 7,
                label: '姓名'
              }]
            }]
          }]
        },
        {
          id: 2,
          label: '广东',
          children: [{
            id: 4,
            label: '化州',
            children: [{
              id: 6,
              label: '林尘镇',
              children: [{
                id: 8,
                label: '英歌村',
                disabled: true
              }]
            }]
          }]
        }
      ],
      defaultProps: {
        children: 'children',
        label: 'label'
      }
    }
  },
  mounted () {
    setTimeout(() => {
      this.columnar()
    }, 100)
  },
  methods: {
    columnar () {
      var myChart = this.$echarts.init(this.$refs.box)
      window.addEventListener('resize', () => {
        myChart.resize()
      })
      this.$nextTick(function () {
        var option = {
          title: {
            text: 'Echarts入门示例'
          },
          tooltip: {},
          legend: {
            data: ['销量']
          },
          xAxis: {
            data: ['衬衫', '羊毛衫', '雪纺衫']
          },
          yAxis: {},
          series: [
            {
              name: '销量',
              type: 'bar',
              data: [5, 20, 36, 10, 10, 20]
            }
          ]
        }
        myChart.setOption(option)
      })
    },
    handleNodeClick (data) {
      console.log(data)
    },
    start (node, event) {
      console.log('drag start', node, event)
    },
    enter (node, event) {
      console.log('drag enter', node, event)
    }
  }
}
</script>
<style scoped>
.home {
  width: 100%;
  height: 100%;
  background-color: red;
}
.box {
  width: 100%;
  height: 90%;
  background-color: bisque;
}
</style>
