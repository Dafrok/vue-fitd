<template lang="jade">
div(:class="classes", :style="{display: show ? 'block' : 'none'}", @click="handleOutClick")
  div(:class="extraModalSizeClass", @click="stopBackdropEvent")
    div.modal-content
      div.modal-header(v-text="title", v-if="title")
      div.modal-body
        slot
      div.modal-footer
        slot(name="operate-bar")
          fit-button(@click="handleCancel", type="secondary")
            span(v-text="cancelText")
          fit-button(@click="handleOk", type="primary")
            span(v-text="okText")
</template>

<script>
import FitButton from '../form/button.vue'
export default {
  components: {
    fitButton: FitButton
  },
  props: ['type', 'cancel-text', 'ok-text', 'show', 'title', 'size', 'backdrop-click-to-close'],
  methods: {
    handleOk () {
      this.$emit('ok')
    },
    handleCancel () {
      this.$emit('cancel')
    },
    handleOutClick () {
      if (this.backdropClickToClose) {
        this.handleCancel()
      }
    },
    stopBackdropEvent (e) {
      e.stopPropagation()
    }
  },
  computed: {
    classes () {
      return {
        'modal': true,
        'fade': true,
        'in': true
      }
    },
    extraModalSizeClass () {
      return {
        'modal-dialog': true,
        'modal-lg': this.size === 'large',
        'modal-sm': this.size === 'small'
      }
    },
    okText () {
      return this['ok-text'] || 'Ok'
    },
    cancelText () {
      return this['cancel-text'] || 'Cancel'
    }
  }
}
</script>

<style lang="stylus">

$border-radius = .25rem //!default;
$border-radius-lg = .3rem //!default;
$border-radius-sm = .2rem //!default;
$line-height = 1.5 //!default;

// Modals

// Padding applied to the modal body
$modal-inner-padding = 15px //!default;

$modal-title-padding = 15px //!default;
$modal-title-line-height = $line-height //!default;

$modal-content-bg = #fff //!default;
$modal-content-border-color = rgba(0, 0, 0, .2) //!default;

$modal-backdrop-bg = #000 //!default;
$modal-backdrop-opacity = .5 //!default;
$modal-header-border-color = #e5e5e5 //!default;
$modal-footer-border-color = $modal-header-border-color //!default;

$modal-lg = 900px //!default;
$modal-md = 600px //!default;
$modal-sm = 300px //!default;

.modal
    overflow-x: hidden;
    overflow-y: auto;
    background: rgba(0, 0, 0, .35);


.close
    float: right;
    font-size: 1.5rem;
    font-weight: 700;
    line-height: 1;
    color: #000;
    text-shadow: 0 1px 0 #fff;
    opacity: .2;
    padding: 0;
    cursor: pointer;
    background: transparent;
    border: 0;


button.close
    outline: none;
    &:hover
        opacity: .6;



// .modal-open      - body class for killing the scroll
// .modal           - container to scroll within
// .modal-dialog    - positioning shell for the actual modal
// .modal-content   - actual modal w/ bg and corners and shit

// Kill the scroll on the body
&.modal-open
    overflow: hidden;


// Container that the modal scrolls within
&.modal
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 1050;
    display: none;
    // Prevent Chrome on Windows from adding a focus outline. For details, see
    // https://github.com/twbs/bootstrap/pull/10951.
    outline: 0;
    -webkit-overflow-scrolling: touch;

    // When fading in the modal, animate it to slide down
    &.fade .modal-dialog
        transition: transform .3s ease-out;
        transform: translate(0, -25%);

    &.in .modal-dialog
        transform: translate(0, 0);



.modal-open .modal
    overflow-x: hidden;
    overflow-y: auto;


// Shell div to position the modal with bottom padding
.modal-dialog
    position: relative;
    width: auto;
    margin: 10px;


// Actual modal
.modal-content
    position: relative;
    background-color: $modal-content-bg;
    background-clip: padding-box;
    box-shadow: 0 0 50px #ccc;
    border-radius: $border-radius-lg;
    outline: 0;


// Modal background
.modal-backdrop
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 1040;
    background-color: $modal-backdrop-bg;

    // Fade for backdrop
    &.fade
        opacity: 0;

    &.in
        opacity: $modal-backdrop-opacity;



// Modal header
// Top section of the modal w/ title and dismiss
.modal-header
    padding: $modal-title-padding;
    border-bottom: 1px solid $modal-header-border-color;
    @include clearfix;


// Close icon
.modal-header .close
    margin-top: -2px;


// Title text within header
.modal-title
    margin: 0;
    line-height: $modal-title-line-height;


// Modal body
// Where all modal content resides (sibling of .modal-header and .modal-footer)
.modal-body
    position: relative;
    padding: $modal-inner-padding;


// Footer (for actions)
.modal-footer
    padding: $modal-inner-padding;
    text-align: right; // right align buttons
    border-top: 1px solid $modal-footer-border-color;
    @include clearfix(); // clear it in case folks use .pull-* classes on buttons

    // Properly space out buttons
    .btn + .btn
        margin-bottom: 0; // account for input[type="submit"] which gets the bottom margin like all other inputs
        margin-left: 5px;

    // but override that for button groups
    .btn-group .btn + .btn
        margin-left: -1px;

    // and override it for block buttons as well
    .btn-block + .btn-block
        margin-left: 0;



// Measure scrollbar width for padding body during modal show/hide
.modal-scrollbar-measure
    position: absolute;
    top: -9999px;
    width: 50px;
    height: 50px;
    overflow: scroll;


// Automatically set modal's width for larger viewports
.modal-dialog
    width: $modal-md;
    margin: 30px auto;


// Modal sizes
.modal-sm
    width: $modal-sm;


.modal-lg
    width: $modal-lg;


</style>
