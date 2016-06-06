<template lang="jade">
div.fit-layout-global-sidebar(:style="style")
  slot
</template>

<script>
export default {
  props: ['width'],
  watch: {
    width (val) {
      this.$parent.$set('sidebarWidth', this.width)
    }
  }
}
</script>

<style lang="stylus" scoped>
.fit-layout-global-sidebar
  box-sizing border-box
  width 100%
  height 100%
  z-index 3
</style>
