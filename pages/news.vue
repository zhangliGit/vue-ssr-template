<template>
  <div class="news">
    <img class="banner-top" src="../assets/img/banner_zxzx.png" alt="" />
    <div class="content-w">
      <div class="u-auto">
        <ul class="news-tab">
          <li
            v-for="(item, index) in tabList"
            :key="index"
            :class="{ act: current === index }"
            @click="changeTag(index)"
          >
            {{ item }}
          </li>
        </ul>
      </div>
      <div class="u-padd-b20 u-padd-t20">
        <div v-show="current === 0" class="news-list">
          <div v-for="item in newsList" :key="item._id" class="news-item u-fx">
            <div class="date">{{ item.showDate }}</div>
            <div class="u-fx-f1">
              <div class="title u-te">{{ item.title }}</div>
              <div class="level-title u-te2">{{ item.levelTitle }}</div>
            </div>
            <div class="hidden-xs-only hidden-sm-only hidden-md-only">
              <img :src="item.url" alt="" />
            </div>
          </div>
        </div>
        <div v-show="current === 1" class="org-list">
          <el-row class="org-item">
            <el-col :xs="12" :sm="8" :lg="4">1</el-col>
            <el-col :xs="12" :sm="8" :lg="4">2</el-col>
            <el-col :xs="12" :sm="8" :lg="4">3</el-col>
            <el-col :xs="12" :sm="8" :lg="4">4</el-col>
            <el-col :xs="12" :sm="8" :lg="4">5</el-col>
            <el-col :xs="12" :sm="8" :lg="4">6</el-col>
          </el-row>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'News',
  async asyncData({ $axios }) {
    const res = await $axios.get(
      `http://canpointtest.com:8090/videoApi/getNews?page=1&size=20`
    )
    console.log(res.data.data)
    return { newsList: res.data.data }
  },
  data() {
    return {
      tabList: ['新闻动态', '政府政策'],
      current: 0,
      newsList: [],
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
.news {
  .news-tab {
    width: 240px;
    margin: 2rem auto 3rem auto;
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
  .news-item {
    padding: 15px;
    cursor: pointer;
    transition: all 0.2s ease;
    border-bottom: 1px #f5f5f5 solid;
    .date {
      margin-right: 30px;
      font-size: 24px;
      letter-spacing: 2px;
    }
    .title {
      font-size: 18px;
    }
    .level-title {
      font-size: 14px;
      margin-top: 20px;
    }
    img {
      width: 200px;
      height: 150px;
      display: block;
    }
    &:hover {
      transform: scale(0.98);
    }
  }
}
</style>
