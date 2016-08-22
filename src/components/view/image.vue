<template lang="jade">
div.image-wrapper(:style="wrapperStyle")
  img(:src="src", :style="{display: 'none'}", @load="onImageLoad")
</template>

<script>
export default {
  props: {
    'src': {},
    'width': {
      default: 200
    },
    'height': {
      default: 200
    }
  },
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
      console.log(this.imageWidth, this.imageHeight)
    }
  },
  computed: {
    wrapperStyle () {
      if (this.imageWidth > this.imageHeight) {
        return {
          backgroundImage: 'url(' + this.src + ')',
          backgroundSize: 'auto ' + this.height + 'px',
          backgroundPosition: '-' + ((this.imageWidth * this.width / this.imageHeight - this.width) / 2) + 'px 0px',
          backgroundRepeat: 'no-repeat',
          width: this.width + 'px',
          height: this.height + 'px'
        }
      } else {
        return {
          backgroundImage: 'url(' + this.src + ')',
          backgroundSize: this.width + 'px',
          backgroundPosition: '0px -' + ((this.imageHeight * this.width / this.imageWidth - this.width) / 2) + 'px',
          backgroundRepeat: 'no-repeat',
          width: this.width + 'px',
          height: this.height + 'px'
        }
      }
    }
  }
}
</script>

<style>

</style>
