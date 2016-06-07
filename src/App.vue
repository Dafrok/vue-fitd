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
        fit-button(type="success", size="lg", addon-left="trash-o") success
        fit-button(type="warning", addon-right="plus") warning
        fit-button(type="danger", size="sm", addon-left="trash", addon-right="plus-circle") danger
        button-group
          fit-button(type="primary") foo
          fit-button(type="dark") bar
          fit-button(type="success") baz
        button-group(vertical)
          fit-button(type="primary") foo
          fit-button(type="dark") bar
          fit-button(type="success") baz
    layout-col(span="8")
        fit-input(label="This is placeholder.", highlight, direction="left")
</template>

<script>
import {LayoutGlobal, LayoutGlobalHeader, LayoutGlobalFooter, LayoutGlobalSidebar, LayoutGlobalSection, LayoutRow, LayoutCol
  , FitButton, ButtonGroup, FitInput} from './components/index.js'

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
    fitInput: FitInput,
    buttonGroup: ButtonGroup
  }
}
</script>
