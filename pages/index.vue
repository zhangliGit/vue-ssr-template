<template>
  <div class="container-fuild">
    <div class="banner">
      <div v-swiper:mySwiper="swiperOption" class="swiperWrap banner">
        <div class="swiper-wrapper">
          <div class="swiper-slide">
            <img src="../assets/img/banner-one.png" alt />
          </div>
          <div class="swiper-slide">
            <img src="../assets/img/banner-two.png" alt />
          </div>
        </div>
        <div class="swiper-pagination swiper-pagination-bullets"></div>
      </div>
    </div>
    <div class="content-w">
      <div class="title-line">产品选择 / PRODUCT</div>
      <el-row>
        <el-col v-for="(tab, index) in tabData" :key="index" :xs="24" :sm="8" :lg="8" class="show-tab u-fx u-fx-ac-jc">
          <div>
            <img class="" :src="tab.url" alt />
          </div>
          <div class="title">{{ tab.title }}</div>
          <div class="levelTitle">{{ tab.levelTitle }}</div>
        </el-col>
      </el-row>
      <div class="title-line">解决方案 / SOLUTION</div>
      <div class="u-padd-b20 u-padd-t20">
        <el-row :gutter="40">
          <el-col v-for="(solution, index) in solutionList" :key="index" :xs="12" :sm="8" :lg="8" class="box-shadow">
            <img class="solution-img" :src="solution.url" alt />
            <div class="u-fx u-fx-ac u-padd-l10">
              <ul>
                <li class="u-te font-title u-mar-t10">{{ solution.title }}</li>
                <li class="u-te level-title">{{ solution.levelTitle }}</li>
              </ul>
              <div></div>
            </div>
          </el-col>
        </el-row>
      </div>
      <div class="title-line">客户案例 / CASE</div>
      <div class="u-padd-b20 u-padd-t20">
        <el-row :gutter="40">
          <el-col v-for="(item, index) in caseList" :key="index" :xs="12" :sm="8" :lg="6" class="box-shadow">
            <img class="case-img" :src="item.url" alt="" />
            <div class="u-fx u-fx-ac u-padd-l10">
              <ul>
                <li class="u-te font-title u-mar-t10">
                  {{ item.schoolName }}
                </li>
                <li class="u-te level-title">{{ item.systemName }}</li>
              </ul>
              <div></div>
            </div>
          </el-col>
        </el-row>
      </div>
      <div class="title-line">合伙人模式 / PARTNER</div>
      <el-row :gutter="50">
        <el-col class="ywms-bg u-fx u-fx-ae u-fx-jc" :xs="24" :sm="12" :lg="12">
          <div class="model-info">
            <div class="title">业务模式</div>
            <div class="des">直接购买，商业变现，信息集成，智能硬件，总有一款能满足您的要求</div>
            <div><el-button type="primary" size="small">详情</el-button></div>
          </div>
        </el-col>
        <el-col class="hz-bg u-fx u-fx-ae u-fx-jc" :xs="24" :sm="12" :lg="12">
          <div class="model-info">
            <div class="title">合作模式</div>
            <div class="des">可直接作为中间人介绍，也可以获得区域独家代理</div>
            <div><el-button type="primary" size="small">详情</el-button></div>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'
import dataOne from '~/assets/js/index'
export default {
  components: {},
  async asyncData({ $axios }) {
    const resCase = await $axios.get(`http://canpointtest.com:8090/videoApi/getCase?page=1&size=20`)
    const resSolution = await $axios.get(`http://canpointtest.com:8090/videoApi/getSolution?page=1&size=20`)
    return { caseList: resCase.data.data.slice(0, 8), solutionList: resSolution.data.data.slice(0, 6) }
  },
  data() {
    return {
      tabData: dataOne,
      caseList: [],
      solutionList: [],
      swiperOption: {
        loop: true,
        autoplay: 6000,
        slidesPerView: 'auto',
        pagination: {
          el: '.swiper-pagination',
          dynamicBullets: true,
        },
        on: {
          slideChange() {},
          tap() {},
        },
      },
    }
  },
  computed: {
    ...mapState('home', ['title']),
  },
  async mounted() {},
  methods: {
    ...mapActions('home', ['getData']),
    goAbout() {
      this.$router.push('/about')
    },
    goNews() {
      this.$router.push('/news/newList')
    },
  },
}
</script>

<style lang="scss" scoped>
.container-fuild {
  width: 100%;
  margin: 0 auto;
  .banner {
    img {
      width: 100%;
      height: auto;
    }
  }
  .level-title-line {
    text-align: center;
    padding: 0.2rem 0;
    color: #666;
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
    padding-bottom: 0.5rem;
    img {
      width: 2rem;
      height: 2rem;
      display: block;
    }
    .title {
      font-size: 18px;
      font-weight: bold;
      padding: 20px 0;
    }
    .levelTitle {
      font-size: 14px;
      color: #666;
    }
  }
}
</style>
