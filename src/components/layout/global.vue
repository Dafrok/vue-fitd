<template lang="jade">
div(style="width: 100%; height: 100%")
  slot
</template>

<script>
export default {
  data () {
    return {
      sidebarTop: null,
      sidebarBottom: null,
      sidebarAlign: null,
      sidebarWidth: null,
      headerHeight: null,
      footerHeight: null,
      headerSingleLine: null,
      footerSingleLine: null
    }
  },
  watch: {
    headerSingleLine (val) {
      this.sidebarTop = val ? this.headerHeight : 0
    },
    footerSingleLine (val) {
      this.sidebarBottom = val ? this.footerHeight : 0
    }
  }
}
</script>

<style lang="stylus">
html, body, div, span, applet, object, iframe, h1, h2, h3, h4, h5, h6, p, blockquote, pre, a, abbr, acronym, address, big, cite, code, del, dfn, em, img, ins, kbd, q, s, samp, small, strike, strong, sub, sup, tt, var, b, u, i, center, dl, dt, dd, ol, ul, li, fieldset, form, label, legend, table, caption, tbody, tfoot, thead, tr, th, td, article, aside, canvas, details, embed, figure, figcaption, footer, header, hgroup, menu, nav, output, ruby, section, summary, time, mark, audio, video
  margin 0
  padding 0
  border 0
  font-size 100%
  font inherit
  vertical-align baseline
article, aside, details, figcaption, figure, footer, header, hgroup, menu, nav, section
  display block
body
  line-height 1
ol, ul
  list-style none
blockquote, q
  quotes none
blockquote:before, blockquote:after, q:before, q:after
  content ''
  content none
table
  border-collapse collapse
  border-spacing 0
html, body
  width 100%
  height 100%
  overflow hidden
</style>
