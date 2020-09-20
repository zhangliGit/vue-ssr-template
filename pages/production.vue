<template>
  <div class="production">
    <div class="">
      <img class="banner-top" src="../assets/img/banner_cpzx.png" alt="" />
    </div>
    <div class="content-w">
      <div class="u-padd-b20 u-padd-t20">
        <el-row>
          <el-col :xs="24" :sm="12" :lg="12">
            <img class="cpys-img" src="../assets/img/cpys.png" alt="" />
          </el-col>
          <el-col :xs="24" :sm="12" :lg="12">
            <ul class="product-top">
              <li>
                <div class="title">1. 渠道优势</div>
                <div>27年教育行业耕耘，6000家渠道合作伙伴，全品的品牌影响力。</div>
              </li>
              <li>
                <div class="title">2. 服务优势</div>
                <div>
                  遍布全国各地的办事处，定期的培训会；有完整的售前技术支持、行业经验丰富的项目经理指导安装施工、千万级实战项目的售后服务团队。
                </div>
              </li>
              <li>
                <div class="title">3. 技术优势</div>
                <div>复杂环境下远距离毫秒级多人同时动态人脸识别；物联网平台，百万终端设备直连云端。</div>
              </li>
              <li>
                <div class="title">4. 总部支持</div>
                <div>
                  样板校：选择了有代表性的产品推到学校，并且通过web端，微信端让学校常态化使用，
                  通过平台直接排斥了其他竞争公司的进入。
                </div>
                <div>单兵系统：独立可运行的轻量级系统，通电开机，并插入网线即可实际使用。</div>
                <div>
                  300套样机：针对公司、企业、机构、学校都可以直接销售，样机包括识别一体机、人脸识别面板机、人脸访客机和电子班牌。可实现考勤、门禁、访客、信息发布通知等功能
                  服务支持：客户方负责提供项目需求，全品公司负责方案的整理；方案确定后，全品公司负责对项目进行跟进、实施、安装、施工等；项目安装完成后，全品公司负责对项目进行验收和售后服务。
                </div>
              </li>
            </ul>
          </el-col>
        </el-row>
        <div class="title-line">硬件产品 / HARDWARE</div>
        <div class="u-padd-b20 u-padd-t20">
          <el-row :gutter="40">
            <el-col
              v-for="(product, index) in productList"
              :key="index"
              :xs="24"
              :sm="12"
              :lg="12"
              class="product-list"
            >
              <img class="product-img" :src="product.url" alt="" @click="goDetail" />
              <div class="product-des">{{ product.title }}</div>
            </el-col>
          </el-row>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Production',
  async asyncData({ $axios }) {
    const res = await $axios.get(`http://canpointtest.com:8090/videoApi/getSolution?page=1&size=20`)
    return { productList: res.data.data }
  },
  data() {
    return {
      productList: [],
    }
  },
  methods: {
    goDetail() {
      alert(2)
      this.$router.push('/productDetail')
    },
  },
}
</script>
<style lang="scss" scopde>
.production {
  li {
    line-height: 30px;
  }
  .title {
    font-size: 16px;
    margin-top: 30px;
    font-weight: bold;
  }
  .product-list {
    padding: 10px 60px;
  }
  .cpys-img {
    width: 100%;
    height: auto;
    display: block;
  }
  .product-des {
    font-size: 16px;
    height: 40px;
    line-height: 40px;
    background-color: #444;
    color: #fff;
    text-align: center;
  }
}
</style>
