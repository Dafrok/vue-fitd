<template lang="jade">
div(:class="classes")
  slot
</template>

<script>
export default {
  props: ['type', 'justify', 'align'],
  computed: {
    classes () {
      return {
        'fit-layout-row': true,
        'row': true,
        ['row-' + this.type]: this.type,
        ['row-' + this.type + '-' + this.justify]: this.justify,
        ['row-' + this.type + '-' + this.align]: this.align
      }
    }
  }
}
</script>

<style lang="stylus">
.fit-layout-row
  box-sizing border-box
  .fit-layout-row::before, .fit-layout-row::after
    content ""
    display table
  .fit-layout-row::after
    clear both

.fit-layout-row.row
  position relative
  width 100%
  margin-left 0
  margin-right 0
  height auto
  display block

.fit-layout-row.row-flex
  display -webkit-box
  display -webkit-flex
  display -ms-flexbox
  display flex
  -webkit-box-orient horizontal
  -webkit-box-direction normal
  -webkit-flex-direction row
  -ms-flex-direction row
  flex-direction row
  -webkit-flex-wrap wrap
  -ms-flex-wrap wrap
  flex-wrap wrap

.fit-layout-row.row-flex::before, .fit-layout-row.row-flex::after
  display -webkit-box
  display -webkit-flex
  display -ms-flexbox
  display flex

.fit-layout-row.row-flex-start
  -webkit-box-pack start
  -webkit-justify-content flex-start
  -ms-flex-pack start
  justify-content flex-start

.fit-layout-row.row-flex-center
  -webkit-box-pack center
  -webkit-justify-content center
  -ms-flex-pack center
  justify-content center

.fit-layout-row.row-flex-end
  -webkit-box-pack end
  -webkit-justify-content flex-end
  -ms-flex-pack end
  justify-content flex-end

.fit-layout-row.row-flex-space-between
  -webkit-box-pack justify
  -webkit-justify-content space-between
  -ms-flex-pack justify
  justify-content space-between

.fit-layout-row.row-flex-space-around
  -webkit-justify-content space-around
  -ms-flex-pack distribute
  justify-content space-around

.fit-layout-row.row-flex-top
  -webkit-box-align start
  -webkit-align-items flex-start
  -ms-flex-align start
  -ms-grid-row-align flex-start
  align-items flex-start

.fit-layout-row.row-flex-middle
  -webkit-box-align center
  -webkit-align-items center
  -ms-flex-align center
  -ms-grid-row-align center
  align-items center

.fit-layout-row.row-flex-bottom
  -webkit-box-align end
  -webkit-align-items flex-end
  -ms-flex-align end
  -ms-grid-row-align flex-end
  align-items flex-end
</style>
