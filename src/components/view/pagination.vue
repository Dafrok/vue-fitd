<template lang="jade">
button-group
  fit-button(@click="handleChange(currentPage - 1, !hasPrevious || loading, 'before')", v-bind:disabled="!hasPrevious", v-bind:loading="isPreviousLoading") 上一页
  fit-button(@click="handleChange(currentPage + 1, !hasNext || loading, 'after')", v-bind:disabled="!hasNext", v-bind:loading="isNextLoading") 下一页
</template>

<script>
import Vue from 'vue'
import FitButton from '../form/button.vue'
import ButtonGroup from '../form/button-group.vue'

export default {
  props: ['default-page', 'loading', 'next'],
  data () {
    return {
      currentPage: this.defaultPage
    }
  },
  components: {
    fitButton: FitButton,
    buttonGroup: ButtonGroup
  },
  computed: {
    hasNext () {
      return typeof this.next === 'undefined' ? true : this.next
    },
    hasPrevious () {
      return this.currentPage !== 1
    },
    isPreviousLoading () {
      return this.activeButtonName === 'before' && this.loading
    },
    isNextLoading () {
      return this.activeButtonName === 'after' && this.loading
    }
  },
  methods: {
    handleChange (page, disable, activeButtonName) {
      console.log(this.isNextLoading)
      if (!disable) {
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

</style>
