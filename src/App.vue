<template lang="jade">
layout-global
  layout-global-header(slot="header", height="300px", single-line)
    div(style="width: 100%; height:100%; background: red")
  layout-global-footer(slot="footer", height="300px", single-line)
    div(style="width: 100%; height:100%; background: blue")
  layout-global-sidebar(slot="rightbar", width="200px")
    div(style="width: 100%; height:100%; background: yellow")
  layout-global-sidebar(slot="leftbar", width="100px")
    div(style="width: 100%; height:100%; background: green")
    fit-input(label="This is placeholder.", highlight, direction="center", validateMiddleware="validateMiddleware")
      div(slot="rightRender") 233
      div(slot="innerRender")
</template>

<script>
import {LayoutGlobal, LayoutGlobalHeader, LayoutGlobalFooter, LayoutGlobalSidebar, FitInput} from './components/index.js'
export default {
  components: {
    fitInput: FitInput,
    layoutGlobal: LayoutGlobal,
    layoutGlobalHeader: LayoutGlobalHeader,
    layoutGlobalFooter: LayoutGlobalFooter,
    layoutGlobalSidebar: LayoutGlobalSidebar
  }
}
</script>
