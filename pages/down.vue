<template>
  <div class="down">
    <img class="banner-top" src="../assets/img/banner_down.png" alt="" />
    <div class="content-w">
      <div class="u-padd-b20 u-padd-t20">
        <el-row :gutter="40">
          <el-col v-for="i in 4" :key="i" :xs="24" :sm="12" :lg="12" class="u-fx down-list">
            <div>
              <img src="../assets/img/bg1.jpg" alt="" />
            </div>
            <div class="u-fx-f1 u-fx u-fx-ver">
              <div class="title">解决方案类文件</div>
              <div class="info u-fx-f1">包括：校大门管理、宿舍管理、教室测温、食堂刷脸、周界预警方案</div>
              <div class="u-tx-r"><el-button type="primary" size="small">点击下载</el-button></div>
            </div>
          </el-col>
        </el-row>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Down',
  data() {
    return {
      solutionList: [],
    }
  },
}
</script>
<style lang="scss" scoped>
.down-list {
  padding: 20px;
  box-shadow: 0 0 4px #eee;
  .title {
    font-size: 18px;
    font-weight: bold;
  }
  .info {
    padding: 15px 0;
    color: #666;
    line-height: 24px;
  }
  img {
    margin-right: 15px;
    width: 2.5rem;
    height: auto;
    display: block;
  }
}
</style>
