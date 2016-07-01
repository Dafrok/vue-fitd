<template lang="jade">
nav.fit-pagination-pagination-full
  button-group.pagination
    fit-button.before <
    fit-button.after >
    fit-input.inline-input(v-if="enableJump")
    fit-button(v-if="enableJump") 跳转
</template>

<script>
import Vue from 'vue'
import FitInput from '../form/input.vue'
import FitButton from '../form/button.vue'
import ButtonGroup from '../form/button-group.vue'

export default {
  props: ['default-page', 'all-page', 'enable-jump'],
  data () {
    return {
      currentPage: this.defaultPage
    }
  },
  components: {
    fitInput: FitInput,
    fitButton: FitButton,
    buttonGroup: ButtonGroup
  },
  methods: {
    handleChange (page, disable, activeButtonName) {
      if (!disable) {
        let tempPage = this.currentPage
        this.prevPage = tempPage
        this.currentPage = page
        this.activeButtonName = activeButtonName
        Vue.nextTick(() => {
          this.$emit('change', this.currentPage)
        })
      }
    }
  }
}
</script>

<style>
.fit-pagination-pagination-full .pagination {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex; }
  .fit-pagination-pagination-full .pagination .loading {
    width: 14px;
    height: 14px; }
  .fit-pagination-pagination-full .pagination .before .loading {
    margin-right: 5px; }
  .fit-pagination-pagination-full .pagination .after .loading {
    margin-left: 5px; }

.fit-pagination-pagination-full .inline-input {
  display: inline-block;
  float: left;
  margin: 0; }
  .fit-pagination-pagination-full .inline-input .input {
    padding: 7px 10px 7px 10px; width: 100px; }
</style>
