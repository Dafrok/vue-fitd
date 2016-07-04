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
  watch: {
    defaultPage (newVal, oldVal) {
      this.currentPage = newVal
    },
    loading (newVal, oldVal) {
      !newVal && (this.activeButtonName = null)
    }
  },
  computed: {
    hasNext () {
      return typeof this.next === 'undefined' ? true : this.next
    },
    hasPrevious () {
      return this.currentPage !== 1
    },
    isPreviousLoading () {
      const active = (this.activeButtonName === 'before')
      const loading = this.loading
      return active && loading
    },
    isNextLoading () {
      const active = (this.activeButtonName === 'after')
      const loading = this.loading
      return active && loading
    }
  },
  methods: {
    // jump (page) {
    //   let activeButtonName
    //   if (page === this.currentPage) {
    //     return
    //   }
    //   if (page > this.currentPage) {
    //     if (!this.props.next) {
    //       return
    //     }
    //     activeButtonName = 'after'
    //   }
    //   if (page < this.currentPage) {
    //     activeButtonName = 'before'
    //   }
    //   this.handleChange(page, false, activeButtonName)
    // },
    handleChange (page, disable, activeButtonName) {
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
