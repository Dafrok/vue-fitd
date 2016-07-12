<template lang="jade">
layout-global
  layout-global-header(height="20px", single-line)
    div(style="width: 100%; height:100%; background: red")
  layout-global-footer(height="40px")
    pagination-full(enable-jump, :default-page="page", all-page="100", @change="changePage", :loading="paginationLoading")
  layout-global-sidebar(width="50px", align="left")
    div(style="width: 100%; height:100%; background: green")
  layout-global-section
    layout-row
      layout-col(span="8")
        fit-input(label="This is placeholder.", highlight, direction="left")
        modal(:show="showModal", @ok="closeModal", @cancel="closeModal", backdrop-click-to-close, title="Title") text
      layout-col(span="8")
        fit-button(active) default
        fit-button(type="primary", rounded, loading) primary
        fit-button(type="success", size="lg", addon-left="trash-o", @click="openMessage") success
        fit-button(type="warning", addon-right="plus", disabled) warning
        fit-button(type="danger", size="sm", loading) danger
        button-group
          fit-button(type="primary") foo
          fit-button(type="dark") bar
          fit-button(type="success") baz
        button-group(vertical)
          fit-button(type="primary") foo
          fit-button(type="dark") bar
          fit-button(type="success") baz
    layout-col(span="8")
        fit-button(type="primary", @click="openModal") Open Modal
        pagination(:default-page="page", :loading="paginationLoading", @change="changePage")
        span(v-text="page")
        message(:show="showMessage", type="info") Message
</template>

<script>
import {LayoutGlobal, LayoutGlobalHeader, LayoutGlobalFooter, LayoutGlobalSidebar, LayoutGlobalSection, LayoutRow, LayoutCol
  , FitButton, ButtonGroup, FitInput, Modal, Pagination, PaginationFull, Message} from './components/index.js'

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
    buttonGroup: ButtonGroup,
    modal: Modal,
    pagination: Pagination,
    paginationFull: PaginationFull,
    message: Message
  },
  data () {
    return {
      showModal: false,
      showMessage: false,
      page: 1,
      paginationLoading: false
    }
  },
  methods: {
    openMessage () {
      this.showMessage = true
    },
    openModal () {
      this.showModal = true
    },
    closeModal () {
      this.showModal = false
    },
    changePage (page) {
      this.paginationLoading = true
      setTimeout(() => {
        this.page = page
        this.paginationLoading = false
      }, 2000)
    }
  }
}
</script>
