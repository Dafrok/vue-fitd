<template lang="jade">
div.fit-layout-global-sidebar(:style="style")
  slot
</template>

<script>
export default {
  props: ['width', 'align'],
  computed: {
    style () {
      const isLeft = !(this.align === 'right')
      return {
        position: 'absolute',
        width: this.width,
        left: isLeft ? 0 : 'auto',
        right: isLeft ? 'auto' : 0,
        bottom: this.$parent.sidebarBottom,
        top: this.$parent.sidebarTop
      }
    }
  },
  ready () {
    this.$parent.$set('sidebarWidth', this.width)
    this.$parent.$set('sidebarAlign', this.align)
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
