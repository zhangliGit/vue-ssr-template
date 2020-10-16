<template>
  <div class="container-fuild">
    <div class="banner">
      <div v-swiper:mySwiper="swiperOption" class="swiperWrap">
        <div class="swiper-wrapper">
          <div v-for="(banner, index) in bannerList" :key="index" class="swiper-slide" @click="goDetial(index)">
            <img :src="banner.url" />
          </div>
        </div>
        <div class="swiper-pagination swiper-pagination-bullets"></div>
      </div>
    </div>
    <div class="cpxz-box">
      <div class="content-w">
        <div class="title-line">产品选择 / PRODUCT</div>
        <el-row :gutter="20">
          <el-col
            v-for="(tab, index) in tabData"
            :key="index"
            :xs="8"
            :sm="8"
            :lg="8"
            class="show-tab u-hand u-fx u-fx-ac-jc animate_animated animate_fadeIn"
            @click.native="goProduct(index)"
          >
            <div>
              <img class="product-tab-img" :src="tab.url" alt />
            </div>
            <div class="title">{{ tab.title }}</div>
            <div class="levelTitle">{{ tab.levelTitle }}</div>
          </el-col>
        </el-row>
      </div>
    </div>
    <div class="jjfa-box">
      <div class="content-w">
        <div class="title-line">解决方案 / SOLUTION</div>
        <div class="u-tx-c level-title-line u-font-2">累计为超过2000家学校提供安防技术解决方案或咨询服务</div>
        <el-row :gutter="40">
          <el-col
            v-for="(solution, index) in solutionList"
            :key="index"
            :xs="12"
            :sm="8"
            :lg="8"
            class="box-shadow u-hand u-bg-fff"
            @click.native="goSolution(solution._id)"
          >
            <div class="solution-img u-of hand-hover">
              <img class="solution-img" :src="solution.url" alt />
            </div>
            <div class="u-fx u-fx-ac u-padd-l10 u-padd-t20">
              <ul class="u-fx-f1">
                <li class="u-te font-title">{{ solution.title }}</li>
                <li class="u-te level-title">{{ solution.levelTitle }}</li>
              </ul>
              <div class="rit-arrow"></div>
            </div>
          </el-col>
        </el-row>
        <div class="more-btn" @click="goHtml('/case', 3)">查看更多</div>
      </div>
    </div>
    <div class="khal-box">
      <div class="content-w">
        <div class="title-line">客户案例 / CASE</div>
        <el-row :gutter="40">
          <el-col
            v-for="(item, index) in caseList"
            :key="index"
            :xs="12"
            :sm="8"
            :lg="6"
            class="box-shadow u-hand u-bg-fff"
            @click.native="goCase(item._id)"
          >
            <div class="case-img u-of hand-case">
              <div class="show-info">
                <div class="u-pos-box u-fx-ac-jc">
                  <div class="case-name">{{ item.schoolName }}</div>
                  <div class="case-system">{{ item.systemName }}</div>
                  <div class="case-info">{{ item.systemDes }}</div>
                  <div>
                    <el-button type="primary" size="small">详情</el-button>
                  </div>
                </div>
              </div>
              <img class="case-img" :src="item.url" alt />
            </div>
            <div class="u-fx u-fx-ac u-padd-l10 u-padd-t20">
              <ul class="u-fx-f1">
                <li class="u-te font-title">{{ item.schoolName }}</li>
                <li class="u-te level-title">{{ item.systemName }}</li>
              </ul>
              <div class="rit-arrow"></div>
            </div>
          </el-col>
        </el-row>
        <div class="more-btn" @click="goHtml('/case', 4)">查看更多</div>
      </div>
    </div>
    <div class="hhrms-box hidden-md-and-down">
      <div class="content-w">
        <div class="title-line">合伙人模式 / PARTNER</div>
        <el-row :gutter="50">
          <el-col class="ywms-bg u-fx u-fx-ae u-fx-jc" :xs="24" :sm="12" :lg="12">
            <div class="model-info">
              <div class="title">业务模式</div>
              <div class="des">直接购买，商业变现,信息集成，智能硬件</div>
              <div class="des">总有一款能满足您的要求</div>
              <div class="btn-top">
                <el-button type="primary" size="small" @click="goHtml('/model', 5)">详情</el-button>
              </div>
            </div>
          </el-col>
          <el-col class="hz-bg u-fx u-fx-ae u-fx-jc" :xs="24" :sm="12" :lg="12">
            <div class="model-info">
              <div class="title">合作模式</div>
              <div class="des">可直接作为中间人介绍</div>
              <div class="des">也可以获得区域独家代理</div>
              <div class="btn-top">
                <el-button type="primary" size="small" @click="goHtml('/model', 5)">详情</el-button>
              </div>
            </div>
          </el-col>
        </el-row>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'
import dataOne from '~/assets/js/index'
export default {
  async asyncData({ $axios }) {
    const resBanner = await $axios.get(`http://canpointtest.com:8090/videoApi/getBanner?page=1&size=20`)
    const resCase = await $axios.get(`http://canpointtest.com:8090/videoApi/getCase?page=1&size=20`)
    const resSolution = await $axios.get(`http://canpointtest.com:8090/videoApi/getSolution?page=1&size=20`)
    return {
      caseList: resCase.data.data.slice(0, 8),
      solutionList: resSolution.data.data.slice(0, 6),
      bannerList: resBanner.data.data,
    }
  },
  data() {
    return {
      tabData: dataOne,
      caseList: [],
      solutionList: [],
      bannerList: [],
      swiperOption: {
        autoplay: 4000,
        loop: true,
      },
    }
  },
  computed: {
    ...mapState('home', ['title']),
  },
  mounted() {
    ;(function () {
      const hm = document.createElement('script')
      hm.src = 'https://hm.baidu.com/hm.js?29a13c7ed5518103e11246e1ec3932d8'
      const s = document.getElementsByTagName('script')[0]
      s.parentNode.insertBefore(hm, s)
    })()
  },
  methods: {
    ...mapActions('home', ['getData']),
    goDetial(index) {
      if (index === 0) {
        this.$store.commit('home/SET_Data', 3)
        this.goSolution('5f5ede27da5ef91caf4dd302')
      } else {
        this.$store.commit('home/SET_Data', 2)
        this.$router.push('/video')
      }
    },
    goProduct(index) {
      if (index === 0) {
        this.$store.commit('home/SET_Data', 1)
        this.$router.push('/production')
      } else if (index === 1) {
        this.$store.commit('home/SET_Data', 1)
        this.$router.push('/production')
      } else {
        this.$store.commit('home/SET_Data', 2)
        this.$router.push('/video')
      }
    },
    goCase(_id) {
      this.$store.commit('home/SET_Data', 4)
      this.$router.push({
        path: 'caseDetail',
        query: {
          _id,
        },
      })
    },
    goSolution(_id) {
      this.$store.commit('home/SET_Data', 3)
      this.$router.push({
        path: 'solutionDetail',
        query: {
          _id,
        },
      })
    },
    goHtml(path, index) {
      this.$store.commit('home/SET_Data', index)
      this.$router.push(path)
    },
  },
}
</script>

<style lang="scss" scoped>
.container-fuild {
  width: 100%;
  margin: 0 auto;
  .swiper {
    height: 300px;
    width: 100%;
    .swiper-slide {
      text-align: center;
      font-size: 38px;
      font-weight: 700;
      background-color: #eee;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .swiper-pagination {
      > .swiper-pagination-bullet {
        background-color: red;
      }
    }
  }
  .banner {
    img {
      width: 100%;
      height: auto;
    }
  }
  .btn-top {
    margin-top: 60px;
    margin-bottom: 40px;
  }
  .more-btn {
    margin: 35px auto 0 auto;
    height: 60px;
    width: 180px;
    background-color: #eee;
    letter-spacing: 2px;
    text-align: center;
    line-height: 60px;
    color: #666;
    font-size: 14px;
    cursor: pointer;
  }
  .more-btn:hover {
    background-color: #4b6fd3;
    color: #fff;
  }
  .level-title-line {
    text-align: center;
    padding: 0.2rem 0;
    font-size: 14px;
    letter-spacing: 2px;
    color: #999;
  }
  .model-info {
    text-align: center;
    padding-bottom: 60px;
    line-height: 40px;
    .title {
      font-size: 22px;
      color: #1fa7e5;
    }
    .des {
      color: #666;
    }
  }
  .show-tab {
    padding: 15px 0;
    .title {
      font-size: 18px;
      font-weight: bold;
      padding: 25px 0;
    }
    .levelTitle {
      font-size: 14px;
      text-align: center;
      color: #666;
    }
  }
}
</style>
