<template>
  <div class="AboutView">
    <div class="box1">
      <div class="title">
        <h3 class="text">{{title}}</h3>
      </div>
      <div class="box2">
        <el-row :gutter='20'>
          <el-col :span='6'>
            <div class="select">
              <el-select
                v-model="value"
                placeholder="请选择"
              >
                <el-option
                  v-for="item in options"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value"
                >
                </el-option>
              </el-select>
            </div>
          </el-col>
          <el-col :span="6">
            时间段：
          </el-col>
          <el-col :span="6">
            <el-select
                v-model="value"
                placeholder="请选择"
              >
                <el-option
                  v-for="item in options2"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value"
                >
                </el-option>
              </el-select>
          </el-col>
          <el-col :span="6">
            <div class="grid-content bg-purple"></div>
          </el-col>
        </el-row>
        <div class="line"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AboutView',
  data () {
    return {
      title: '耗电监控',
      value: '',
      options1: [
        {
          value: 1,
          label: '当天数据'
        },
        {
          value: 2,
          label: '当周数据'
        },
        {
          value: 3,
          label: '当月数据'
        },
        {
          value: 4,
          label: '当年数据'
        }
      ],
      options2: [
        {
          value: 1,
          label: '选择路线'
        },
        {
          value: 2,
          label: '搅拌站'
        },
        {
          value: 3,
          label: '综合站'
        },
        {
          value: 4,
          label: '楼板线'
        }
      ]
    }
  },
  methods: {}
}
</script>

<style lang='scss' scoped>
.AboutView {
  width: 100%;
  height: 100%;
  .box1 {
    width: 80%;
    height: 60%;
    border: 1px solid #333;
    .title {
      border-bottom: 1px solid #333;
      .text {
        margin-left: 10px;
        font-size: 16px;
        font-weight: 550;
      }
    }
    .box2 {
      .select {
      }
      .line {
      }
    }
  }
}
</style>
