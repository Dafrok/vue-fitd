<template lang="jade">
fit-input(label="This is placeholder.", highlight, direction="center", validateMiddleware="validateMiddleware")
  div(slot="rightRender") 233
  div(slot="innerRender")
</template>

<script>
import {FitInput} from './components/index.js'
export default {
  components: {
    fitInput: FitInput
  },
  methods: {
    validateMiddleware () {
      return {}
    }
  }
}
</script>
