<template lang="jade">
div.image-wrapper
  img(:src="src", style="{display: 'none'}", @load="onImageLoad")
</template>

<script>
export default {
  data () {
    return {
      imageLoaded: false,
      imageWidth: null,
      imageHeight: null
    }
  },
  methods: {
    onImageLoad (e) {
      const image = e.target
      this.imageWidth = image.width
      this.imageHeight = image.height
    }
  }
}
</script>

<style>

</style>
