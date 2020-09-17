<template>
  <div class="video">
    <img class="banner-top" src="../assets/img/banner_spzq.png" alt="" />
    <div class="content-w">
      <div class="u-padd-b20 u-padd-t20">
        <el-row :gutter="40">
          <el-col
            v-for="(video, index) in videoList"
            :key="index"
            :xs="12"
            :sm="8"
            :lg="8"
            class="box-shadow"
          >
            <img class="video-img" :src="video.url" alt="" />
            <div class="u-fx u-fx-ac u-padd-l10">
              <ul>
                <li class="u-te font-title u-mar-t10">
                  {{ video.title }}
                </li>
                <li class="u-te level-title">{{ video.levelTitle }}</li>
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
  name: 'Video',
  async asyncData({ $axios }) {
    const res = await $axios.get(
      `http://canpointtest.com:8090/videoApi/getVideo?page=1&size=20`
    )
    console.log(res.data.data)
    return { videoList: res.data.data }
  },
  data() {
    return {
      videoList: [],
    }
  },
}
</script>
