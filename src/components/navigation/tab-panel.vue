<template lang="jade">
div(v-if="active", :class="className")
  slot
</template>

<script>
export default {
  props: ['class-name', 'tab'],
  computed: {
    active () {
      return +this.$parent._data.activeKey === this.$parent.$children.indexOf(this)
    }
  }
}
</script>

<style>

</style>
