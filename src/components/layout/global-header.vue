<template lang="jade">
header.fit-layout-global-header(:style="{height: height}")
  slot
</template>

<script>
export default {
  props: ['height', 'singleLine'],
  ready () {
    this.$parent.headerSingleLine = this.singleLine
    this.$parent.$set('headerHeight', this.height || '100px')
  }
}
</script>

<style lang="stylus" scoped>
.fit-layout-global-header
  box-sizing border-box
  position absolute
  top 0
  left 0
  width 100%
  height 100px
  z-index 3
</style>
