<template>
  <div class="case">
    <Header></Header>
    <Bottom></Bottom>
  </div>
</template>
<script>
import Header from '~/components/Header'
import Bottom from '~/components/Bottom'
export default {
  name: 'Case',
  components: {
    Header,
    Bottom,
  },
}
</script>
