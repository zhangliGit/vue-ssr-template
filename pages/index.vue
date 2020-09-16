<template>
  <div class="container-fuild">
    <div class="banner">
      <img src="../assets/img/banner-one.png" alt="" />
    </div>
    <el-row>
      <el-col :xs="12" :sm="12" :lg="8">1</el-col>
      <el-col :xs="12" :sm="12" :lg="8">2</el-col>
      <el-col :xs="12" :sm="12" :lg="8">3</el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  components: {},
  async asyncData({ $axios }) {
    // const res = await $axios.get(
    //   `http://canpointtest.com:8090/videoApi/getVideo?page=1&size=20`
    // )
  },
  methods: {
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
  background-color: tomato;
  margin: 0 auto;
  .banner {
    img {
      width: 100%;
      height: auto;
    }
  }
}
</style>
