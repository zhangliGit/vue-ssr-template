<template>
  <div class="video">
    <img class="banner-top" src="../assets/img/banner_khal.png" alt="" />
    <div class="content-w">
      <div class="u-padd-b20 u-padd-t20">
        <el-row :gutter="40">
          <el-col v-for="(item, index) in caseList" :key="index" :xs="12" :sm="8" :lg="6" class="box-shadow" @click.native="goDetail(item._id)">
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
    </div>
  </div>
</template>
<script>
export default {
  name: 'Case',
  async asyncData({ $axios }) {
    const res = await $axios.get(`http://canpointtest.com:8090/videoApi/getCase?page=1&size=20`)
    return { caseList: res.data.data }
  },
  data() {
    return {
      caseList: [],
    }
  },
  methods: {
    goDetail(_id) {
      this.$router.push({
        path: 'caseDetail',
        query: {
          _id,
        },
      })
    },
  },
}
</script>
<style lang="scss" scoped>
.case-info {
  color: #fff;
  text-align: center;
  position: absolute;
  z-index: 1;
  width: 98%;
  margin: 0 auto;
  bottom: 30px;
  left: 0;
  letter-spacing: 2px;
  line-height: 20px;
}
</style>
