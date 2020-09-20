<template>
  <div class="production-detail">
    <img class="banner-top" src="../assets/img/banner_cpzx.png" alt="" />
    <div class="content-w">
      <div class="u-padd-b20 u-padd-t20">
        <div class="title-line">硬件产品</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Production',
  async asyncData({ $axios }) {},
  data() {
    return {
      productList: [],
    }
  },
}
</script>
