<template>
  <div>
    <feature-list :type="0" keyword=""></feature-list>
  </div>
</template>
<script>
import List from '../List.vue'
export default {
  data () {
    return {}
  },
  components: {
    'feature-list': List
  }
}
</script>
<style lang="scss" scoped>
</style>
