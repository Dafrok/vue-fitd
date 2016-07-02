<template lang="jade">
div.message
  div.m-layer.z-show
    table
      tbody
        tr
          td
            article.lywrap
              section(:class="typeClass")
                slot
</template>

<script>
import Vue from 'vue'
import FitButton from '../form/button.vue'
import ButtonGroup from '../form/button-group.vue'

export default {
}
</script>

<style>

</style>
