<template lang="jade">
footer.fit-layout-global-footer(:style="style")
  slot
</template>

<script>
export default {
  props: ['height', 'single-line'],
  ready () {
    this.$parent.footerSingleLine = this.singleLine
    this.$parent.$set('footerHeight', this.height || '100px')
  },
  computed: {
    style () {
      const isLeftSidebar = !(this.$parent.sidebarAlign === 'right')
      return {
        width: this.singleLine ? '100%' : 'auto',
        left: this.singleLine ? 'auto' : isLeftSidebar ? this.$parent.sidebarWidth : 0,
        right: this.singleLine ? 'auto' : isLeftSidebar ? 0 : this.$parent.sidebarWidth,
        height: this.height
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
.fit-layout-global-footer
  box-sizing border-box
  position absolute
  left 0
  bottom 0
  height 100px
  z-index 3
</style>
