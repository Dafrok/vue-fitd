<template lang="jade">
header.fit-layout-global-header(:style="style")
  slot
</template>

<script>
export default {
  props: ['height', 'singleLine'],
  ready () {
    this.$parent.headerSingleLine = this.singleLine
    this.$parent.$set('headerHeight', this.height || '100px')
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
.fit-layout-global-header
  box-sizing border-box
  position absolute
  top 0
  left 0
  height 100px
  z-index 3
</style>
