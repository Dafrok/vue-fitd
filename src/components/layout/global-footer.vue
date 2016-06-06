<template lang="jade">
footer.fit-layout-global-footer(:style="{height: height}")
  slot
</template>

<script>
export default {
  props: ['height', 'single-line'],
  ready () {
    this.$parent.footerSingleLine = this.singleLine
    this.$parent.$set('footerHeight', this.height || '100px')
  }
}
</script>

<style lang="stylus" scoped>
.fit-layout-global-footer
  box-sizing border-box
  position absolute
  left 0
  bottom 0
  width 100%
  height 100px
  z-index 3
</style>
