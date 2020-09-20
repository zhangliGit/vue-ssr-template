<template>
  <div class="container-fuild">
    <img class="banner-top" src="../assets/img/banner_gywm.png" alt="" />
    <el-row>
      <el-col :xs="24" :sm="12" :lg="12" class="company-info">
        <div class="company-box">
          <div class="title">公司简介</div>
          <div class="info">
            武汉全品教育科技有限公司，简称“武汉全品”，成立于2017年，注册资金4000万。专注于机器视觉在K12教育领域的应用，为平安校园、
            智慧校园提供软硬件、内容资源一体化的AI+教育解决方案
          </div>
          <div class="info">
            核心团队由资深教育人士、互联网老兵、人工智能专家、多年行业经验的专业技术团队组成，专注于K12教育，
            以技术开发及创新应用为驱动，致力于为数字化教育资源、创新型教育产品、智慧校园整体解决方案的研发运营提供线
            上线下深度融合的教育大数据产品与服务，开启大数据智慧教育新模式！
          </div>
        </div>
      </el-col>
      <el-col :xs="24" :sm="12" :lg="12" class="bg-wenhua"></el-col>
    </el-row>
    <div class="content-w">
      <div class="u-padd-b20 u-padd-t20"></div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'About',
  data() {
    return {
      solutionList: [],
    }
  },
}
</script>
<style lang="scss" scoped>
.company-info {
  height: 5.4rem;
  background-color: #eee;
  .title {
    font-size: 24px;
    font-weight: bold;
  }
  .info {
    color: #666;
    margin-top: 40px;
    line-height: 28px;
  }
}
.bg-wenhua {
  height: 5.4rem;
  background: url(../assets/img/wenhua.png) no-repeat;
  background-size: 100% 100%;
}
</style>
