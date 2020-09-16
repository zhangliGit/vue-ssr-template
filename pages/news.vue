<template>
  <div class="news">
    <Header></Header>
    <Bottom></Bottom>
  </div>
</template>
<script>
import Header from '~/components/Header'
import Bottom from '~/components/Bottom'
export default {
  name: 'News',
  components: {
    Header,
    Bottom,
  },
  data() {
    return {}
  },
  methods: {},
}
</script>
