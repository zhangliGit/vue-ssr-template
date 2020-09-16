<template>
  <div class="solution">
    <Header></Header>
    <Bottom></Bottom>
  </div>
</template>
<script>
import Header from '~/components/Header'
import Bottom from '~/components/Bottom'
export default {
  name: 'Solution',
  components: {
    Header,
    Bottom,
  },
}
</script>
