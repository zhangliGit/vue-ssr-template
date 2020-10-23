<template>
  <div class="container-fuild about">
    <img class="banner-top" src="../assets/img/banner_gywm.png" alt />
    <el-row>
      <el-col :xs="24" :sm="12" :lg="12" class="company-info">
        <div class="about-h company-box">
          <div class="title">公司简介</div>
          <div class="company-des" v-html="company"></div>
        </div>
      </el-col>
      <el-col :xs="24" :sm="12" :lg="12" class="about-h bg-wenhua hidden-md-and-down"></el-col>
    </el-row>
    <el-row>
      <el-col :xs="24" :sm="12" :lg="12">
        <div class="about-h company-rongy u-of">
          <div class="zz-title">荣誉资质</div>
          <div>
            <img class="zz-img" src="../assets/img/zz-one.png" alt />
            <img class="zz-img" src="../assets/img/zz-two.png" alt />
            <img class="zz-img" src="../assets/img/zz-three.png" alt />
            <img class="zz-img" src="../assets/img/zz-four.png" alt />
            <img class="zz-img" src="../assets/img/zz-five.png" alt />
            <img class="zz-img" src="../assets/img/zz-six.png" alt />
          </div>
        </div>
      </el-col>
      <el-col :xs="24" :sm="12" :lg="12" class="about-h bg-rongy"></el-col>
    </el-row>
    <div class="content-w">
      <div class="u-padd-b20">
        <div class="title-line">招聘信息</div>
        <div class="u-auto">
          <el-row class="u-mar-b20">
            <el-col v-for="(boss, index) in bossList" :key="index" :xs="24" :sm="8" :lg="8" class="boss">
              <div class="boss-title">{{ boss.title }}</div>
              <div class="boss-remark">{{ boss.remark }}</div>
              <div v-html="boss.content"></div>
            </el-col>
          </el-row>
        </div>
        <el-row class="u-mar-t20">
          <el-col :xs="24" :sm="8" :lg="8" class="area-list">
            <div class="area-title">区域销售经理</div>
            <div class="area-des" v-html="areaPhone"></div>
          </el-col>
          <el-col :xs="24" :sm="16" :lg="16" class="run-bg"></el-col>
        </el-row>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'About',
  async asyncData({ $axios, query }) {
    const res = await $axios.get(`http://canpointtest.com:8090/videoApi/getAbout?type=about`)
    const bossRes = await $axios.get(`http://canpointtest.com:8090/videoApi/getBoss?page=1&size=20`)
    return {
      bossList: bossRes.data.data,
      company: res.data.data[0].content,
      areaPhone: res.data.data[0].content1,
    }
  },
  data() {
    return {
      bossList: [],
      company: '',
      areaPhone: '',
    }
  },
}
</script>
<style lang="scss" scoped>
.about {
  background-color: #ebebeb;
  .company-des {
    margin-top: 20px;
    p {
      line-height: 60px !important;
    }
  }
  .area-des {
    p {
      line-height: 45px !important;
      color: #fff !important;
    }
  }
  .zz-title {
    font-size: 24px;
    color: #fff;
    font-weight: bold;
  }
  .title {
    font-size: 24px;
    font-weight: bold;
  }
  .info {
    color: #666;
    margin-top: 40px;
    line-height: 28px;
  }
  .boss {
    border-radius: 6px;
    overflow-y: scroll;
    background: #fff;
    height: 600px;
    padding: 30px;
    border: 6px #eee solid;
    box-shadow: inset 0 0 10px #eee;
    transition: all ease 0.3s;
    &:hover {
      transform: scale(0.98);
      background: #f5f5f5;
    }
    .boss-title {
      font-size: 20px;
      font-weight: bold;
      text-align: center;
    }
    .boss-remark {
      padding: 10px 0;
      text-align: center;
    }
  }
  .area-list {
    height: 585px;
    background: url(../assets/img/bg-30.jpg) no-repeat bottom;
    background-size: 100% 215px;
    background-color: #313131;
    color: #fff;
    line-height: 40px;
    padding: 20px 20px;
    .area-title {
      font-size: 18px;
    }
  }
  .run-bg {
    height: 475px;
    background: url(../assets/img/bg-31.png) no-repeat right;
    background-size: 711px 475px;
  }
}
</style>
