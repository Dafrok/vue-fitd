<template lang="jade">
button-group
  fit-button(@click="handleChange(currentPage - 1, !hasPrevious || loading, 'before')", v-bind:disabled="!hasPrevious") 上一页
  fit-button(@click="handleChange(currentPage + 1, !hasNext || loading, 'after')", v-bind:disabled="!hasNext") 下一页
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
    }
  },
  methods: {
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
