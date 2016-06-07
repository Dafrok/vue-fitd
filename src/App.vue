<template lang="jade">
layout-global
  layout-global-header(slot="header", height="300px", single-line)
    div(style="width: 100%; height:100%; background: red")
  layout-global-footer(slot="footer", height="300px")
    div(style="width: 100%; height:100%; background: blue")
  layout-global-sidebar(slot="sidebar", width="233px", align="left")
    div(style="width: 100%; height:100%; background: green")
  layout-global-section(slot="sidebar")
    fit-input(label="This is placeholder.", highlight, direction="center")
      div(slot="rightRender") 233
      div(slot="innerRender")

</template>

<script>
import {LayoutGlobal, LayoutGlobalHeader, LayoutGlobalFooter, LayoutGlobalSidebar, LayoutGlobalSection, FitInput} from './components/index.js'
export default {
  components: {
    fitInput: FitInput,
    layoutGlobal: LayoutGlobal,
    layoutGlobalHeader: LayoutGlobalHeader,
    layoutGlobalFooter: LayoutGlobalFooter,
    layoutGlobalSidebar: LayoutGlobalSidebar,
    layoutGlobalSection: LayoutGlobalSection
  }
}
</script>
