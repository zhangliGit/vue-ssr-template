<template>
  <div class="video">
    <img class="banner-top" src="../assets/img/banner_hhrms.png" alt="" />
    <div class="content-w">
      <div class="u-auto u-padd-b">
        <ul class="news-tab">
          <li v-for="(item, index) in tabList" :key="index" :class="{ act: current === index }" @click="changeTag(index)">
            {{ item }}
          </li>
        </ul>
      </div>
      <el-row>
        <el-col :xs="24" :sm="12" :lg="12"></el-col>
        <el-col></el-col>
      </el-row>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Model',
  data() {
    return {
      current: 0,
      tabList: ['业务模式', '合作模式'],
      solutionList: [],
    }
  },
  methods: {
    changeTag(index) {
      this.current = index
    },
  },
}
</script>
<style lang="scss" scoped>
.news-tab {
  width: 240px;
  margin: 0.5rem auto;
  padding-bottom: 1rem;
  li {
    letter-spacing: 2px;
    float: left;
    width: 120px;
    line-height: 50px;
    height: 50px;
    cursor: pointer;
    text-align: center;
    background-color: #eee;
    &.act {
      background-color: #4b6fd3;
      color: #fff;
      font-size: 14px;
    }
  }
}
</style>
