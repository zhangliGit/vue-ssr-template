<template>
  <div class="header u-fx u-fx-jsb u-fx-ac">
    <img class="logo" src="../assets/img/logo.png" alt="" />
    <ul class="hidden-sm-and-up"></ul>
    <ul class="hidden-xs-only">
      <li
        v-for="(menu, index) in menuList"
        :key="index"
        :class="{ act: current === index }"
        @click="goMenu(menu.path, index)"
      >
        {{ menu.title }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      current: 0,
      menuList: [
        {
          path: '/',
          title: '首页',
        },
        {
          path: '/production',
          title: '产品中心',
        },
        {
          path: '/video',
          title: '视频专区',
        },
        {
          path: '/solution',
          title: '解决方案',
        },
        {
          path: '/case',
          title: '客户案例',
        },
        {
          path: '/model',
          title: '合伙人模式',
        },
        {
          path: '/news',
          title: '最新资讯',
        },
        {
          path: '/down',
          title: '资料下载',
        },
        {
          path: '/about',
          title: '关于我们',
        },
      ],
    }
  },
  methods: {
    goMenu(path, index) {
      this.current = index
      this.$router.push(path)
    },
  },
}
</script>

<style scoped lang="scss">
.header {
  position: absolute;
  z-index: 99;
  top: 0;
  width: 80%;
  left: 10%;
  height: 100px;
  ul {
    li {
      cursor: pointer;
      font-size: 16px;
      float: left;
      color: #fff;
      margin-left: 40px;
      transition: all 0.3s ease;
      &.act {
        color: #fef291;
      }
      &:hover {
        color: #f5f5f5;
        transform: scale(1.1);
      }
    }
  }
}
</style>
