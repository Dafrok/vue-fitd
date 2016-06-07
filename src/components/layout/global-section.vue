<template lang="jade">
div.fit-layout-global-section(:style="style")
  slot
</template>

<script>
export default {
  computed: {
    style () {
      const isLeftSidebar = !(this.$parent.sidebarAlign === 'right')
      return {
        top: this.$parent.headerHeight,
        bottom: this.$parent.footerHeight,
        left: isLeftSidebar ? this.$parent.sidebarWidth : 0,
        right: isLeftSidebar ? 0 : this.$parent.sidebarWidth
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
.fit-layout-global-section
  box-sizing border-box
  overflow-x hidden
  position absolute
</style>
