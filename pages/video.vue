<template>
  <div class="video">
    <img class="banner-top" src="../assets/img/banner_spzq.png" alt="" />
    <div class="module-title">视频专区 / VIDEO ZONE</div>
    <div class="content-w">
      <el-row :gutter="15">
        <el-col v-for="i in 10" :key="i" :xs="12" :sm="8" :lg="8">
          <img class="video-img" src="../assets/img/video.jpg" alt="" />
          <div class="u-fx u-fx-ac">
            <ul>
              <li class="u-te">全品AI食堂刷脸消费系统</li>
              <li class="u-te">全品AI食堂刷脸消费系统</li>
            </ul>
            <div></div>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Video',
}
</script>
<style lang="scss" scoped>
.video {
  .video-img {
    width: 100%;
    max-height: 360px;
    display: block;
  }
}
</style>
