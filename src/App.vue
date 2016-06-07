<template lang="jade">
layout-global
  layout-global-header(height="20px", single-line)
    div(style="width: 100%; height:100%; background: red")
  layout-global-footer(height="20px")
    div(style="width: 100%; height:100%; background: blue")
  layout-global-sidebar(width="50px", align="left")
    div(style="width: 100%; height:100%; background: green")
  layout-global-section
    layout-row
      layout-col(span="8")
        fit-input(label="This is placeholder.", highlight, direction="left")
      layout-col(span="8")
        fit-button default
        fit-button(type="primary") primary
        fit-button(type="success") success
        fit-button(type="warning") warning
        fit-button(type="danger") danger
    layout-col(span="8")
        fit-input(label="This is placeholder.", highlight, direction="left")
</template>

<script>
import {LayoutGlobal, LayoutGlobalHeader, LayoutGlobalFooter, LayoutGlobalSidebar, LayoutGlobalSection, LayoutRow, LayoutCol
  , FitButton, FitInput} from './components/index.js'

export default {
  components: {
    layoutGlobal: LayoutGlobal,
    layoutGlobalHeader: LayoutGlobalHeader,
    layoutGlobalFooter: LayoutGlobalFooter,
    layoutGlobalSidebar: LayoutGlobalSidebar,
    layoutGlobalSection: LayoutGlobalSection,
    layoutRow: LayoutRow,
    layoutCol: LayoutCol,
    fitButton: FitButton,
    fitInput: FitInput
  }
}
</script>
