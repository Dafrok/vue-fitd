<template lang="jade">
nav.fit-pagination-pagination-full
  button-group.pagination
    fit-button.before.pagination-left(@click="handleChange(currentPage - 1, !hasPrevious || loading, 'before')", v-bind:disabled="!hasPrevious || loading", v-bind:loading="isPreviousLoading")
      i.fit-pagination-left
    fit-button(@click="handleChange(page, loading || page === currentPage, page > currentPage ? 'after' : 'before')", v-for="page of middleNumbers", v-bind:class="{active: page === currentPage && !loading}", v-bind:disabled="!page || loading", track-by="$index") {{page || '...'}}
    fit-button.after.pagination-right(@click="handleChange(currentPage + 1, !hasNext || loading, 'after')", v-bind:disabled="!hasNext || loading", v-bind:loading="isNextLoading")
      i.fit-pagination-right
    fit-input.inline-input(v-if="enableJump")
    fit-button(v-if="enableJump") 跳转
</template>

<script>
import Vue from 'vue'
import FitInput from '../form/input.vue'
import FitButton from '../form/button.vue'
import ButtonGroup from '../form/button-group.vue'

export default {
  props: ['default-page', 'all-page', 'enable-jump', 'loading'],
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
  watch: {
    defaultPage (newVal, oldVal) {
      this.currentPage = newVal
    }
  },
  computed: {
    middleNumbers () {
      const all = this.allPage
      const current = this.currentPage

      if (all <= 7) {
        let arrs = []
        for (let i = 0; i < all; i++) {
          arrs.push(i + 1)
        }
        return arrs
      }
      if (current <= 4) {
        return [1, 2, 3, 4, 5, 6, null, all]
      }
      if (all - current < 5) {
        let arr = [1, null]
        for (let i = all - 6; i <= all; i++) {
          arr.push(i)
        }
        return arr
      }
      let arr = [1, null]
      for (let i = current - 2; i <= current + 3; i++) {
        arr.push(i)
      }
      arr.push(null)
      arr.push(all)
      return arr
    },
    hasNext () {
      return this.currentPage !== this.allPage
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
.fit-pagination-left:before, .fit-pagination-right:before {
  font-family: 'fit-pagination';
}
.fit-pagination-left:before {
  content: "\ea1d"; }
.fit-pagination-right:before {
  content: "\ea1c"; }
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
.fit-pagination-pagination-full .pagination i {
  border-right: 0!important;
  width: auto!important;
}
</style>
