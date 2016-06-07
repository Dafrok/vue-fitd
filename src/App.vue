<template lang="jade">
layout-global
  layout-global-header(height="20px", single-line)
    div(style="width: 100%; height:100%; background: red")
  layout-global-footer(height="20px")
    div(style="width: 100%; height:100%; background: blue")
  layout-global-sidebar(width="50px", align="left")
    div(style="width: 100%; height:100%; background: green")
  layout-global-section
    row 123
    fit-input(label="This is placeholder.", highlight, direction="center")
      div(slot="rightRender") 233
      div(slot="innerRender")
</template>

<script>
import {LayoutGlobal, LayoutGlobalHeader, LayoutGlobalFooter, LayoutGlobalSidebar, LayoutGlobalSection, Row, Col, FitInput} from './components/index.js'
export default {
  components: {
    fitInput: FitInput,
    layoutGlobal: LayoutGlobal,
    layoutGlobalHeader: LayoutGlobalHeader,
    layoutGlobalFooter: LayoutGlobalFooter,
    layoutGlobalSidebar: LayoutGlobalSidebar,
    layoutGlobalSection: LayoutGlobalSection,
    row: Row,
    col: Col
  }
}
</script>
