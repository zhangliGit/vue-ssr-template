<template>
  <div>
    <div class="about">我是关于界面</div>
    <div @click="back">返回啦</div>
  </div>
</template>
<script>
export default {
  name: 'About',
  data() {
    return {
      title: '我是关于界面',
    }
  },
  methods: {
    back() {
      this.$router.back()
    },
  },
}
</script>
<style scoped>
.about {
  color: red;
}
</style>
