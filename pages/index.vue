<template>
  <div class="container-fuild">
    <div class="banner">
      <img src="../assets/img/banner-one.png" alt="" />
    </div>
    <el-row>
      <el-col :xs="12" :sm="12" :lg="8">{{ title }}</el-col>
      <el-col :xs="12" :sm="12" :lg="8">{{ tag }}</el-col>
      <el-col :xs="12" :sm="12" :lg="8">3</el-col>
    </el-row>
  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'
export default {
  components: {},
  async asyncData({ $axios }) {
    await $axios.get(
      `http://canpointtest.com:8090/videoApi/getVideo?page=1&size=20`
    )
    return {
      tag: 2,
    }
  },
  data() {
    return {
      tag: '1',
    }
  },
  computed: {
    ...mapState('home', ['title']),
  },
  async mounted() {
    // const res = await this.getData()
    // this.tag = 2
    // console.log(res)
  },
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
