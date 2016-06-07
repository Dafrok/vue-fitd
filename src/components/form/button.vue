<template lang="jade">
button(:class="classes")
  div(class="button-container")
    slot(name="addon-left")
    i(class="fa fa-trash-o btn-addon-left")
    div(class="text-child")
      slot
    i(class="fa fa-trash-o btn-addon-right")
    slot(name="addon-right")
</template>

<script>
export default {
  props: ['type', 'disabled', 'loading', 'rounded', 'size', 'active'],
  computed: {
    classes () {
      const size = {
        Normal: 'nm',
        Large: 'lg',
        ExtraSmall: 'xs',
        Small: 'sm'
      }
      return {
        'fit-button': true,
        'btn': true,
        [`btn-${this.type || 'default'}`]: true,
        'disabled': this.disabled || this.loading === true,
        // 'btn-addon': this.addonLeft || this.addonRight,
        'btn-addon': true,
        'btn-rounded': this.rounded,
        'btn-lg': this.size === size.Large,
        'btn-xs': this.size === size.ExtraSmall,
        'btn-sm': this.size === size.Small,
        'active': this.active
      }
    }
  }
}
</script>

<style lang="stylus">
@font-face
.fit-button ._global
  font-family 'fit-button'
  src url("../../font/fit-button.eot?5jskou")
  src url("../../font/fit-button.eot?5jskou#iefix") format("embedded-opentype"), url("../../font/fit-button.ttf?5jskou") format("truetype"), url("../../font/fit-button.woff?5jskou") format("woff"), url("../../font/fit-button.svg?5jskou#fit-button") format("svg")
  font-weight normal
  font-style normal

.fit-button ._global [class^="fit-button-"], .fit-button ._global [class*=" fit-button-"]
  /* use !important to prevent issues with browser extensions that change fonts */
  font-family 'fit-button' !important
  speak none
  font-style normal
  font-weight normal
  font-variant normal
  text-transform none
  line-height 1
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale

.fit-button ._global .fit-button-loading:before
  content "\e982"

.fit-button
  -webkit-transition opacity .3s
  transition opacity .3s
  font-size 14px
  font-family Source Sans Pro, Helvetica Neue, Helvetica, Arial, sans-serif
  font-weight 500
  -webkit-font-smoothing antialiased
  padding 0
  height 32px
  position relative
  overflow hidden
.fit-button .button-container
  display -webkit-box
  display -webkit-flex
  display -ms-flexbox
  display flex
  -webkit-box-align stretch
  -webkit-align-items stretch
  -ms-flex-align stretch
  align-items stretch
  height 100%
.fit-button .button-container .text-child
  padding 0 15px
  display -webkit-box
  display -webkit-flex
  display -ms-flexbox
  display flex
  -webkit-box-flex 1
  -webkit-flex-grow 1
  -ms-flex-positive 1
  flex-grow 1
  -webkit-box-align center
  -webkit-align-items center
  -ms-flex-align center
  align-items center
  -webkit-box-pack center
  -webkit-justify-content center
  -ms-flex-pack center
  justify-content center
.fit-button .animation-spin
  -webkit-animation fa-spin 2s infinite linear
  animation fa-spin 2s infinite linear

.fit-button .loading-container
  -webkit-transition width .3s
  transition width .3s
  display -webkit-box
  display -webkit-flex
  display -ms-flexbox
  display flex
  -webkit-box-align center
  -webkit-align-items center
  -ms-flex-align center
  align-items center
  -webkit-box-pack center
  -webkit-justify-content center
  -ms-flex-pack center
  justify-content center
  width 0
  overflow hidden
.fit-button .loading-container.show
  width 22px

.fit-button.btn
  display inline-block
  font-weight 500
  border-radius 2px
  outline 0 !important
  border 1px solid transparent
  line-height 1.42857143
  white-space nowrap
  -ms-touch-action manipulation
  touch-action manipulation
  cursor pointer
  -webkit-user-select none
  -moz-user-select none
  -ms-user-select none
  user-select none
.fit-button.btn.disabled
  pointer-events none
  cursor not-allowed
  box-shadow none
  opacity .65

.fit-button.btn-lg
  height 50px

.fit-button.btn-xs
  height 30px

.fit-button.btn-sm
  height 25px

.fit-button.btn-link
  color #58666e
.fit-button.btn-link.active
  box-shadow none

.fit-button.btn-default
  color #58666e
  background-color #fcfdfd
  border-color #dee5e7
  background-color #fff
  border-bottom-color #d8e1e3
  box-shadow 0 1px 1px rgba(90, 90, 90, 0.1)
.fit-button.btn-default .taint
  display block
  position absolute
  background rgba(0, 0, 0, 0.1)
  border-radius 100%
  -webkit-transform scale(0)
  transform scale(0)
.fit-button.btn-default .taint.drop
  -webkit-animation fit-button-ripple 0.65s linear
  animation fit-button-ripple 0.65s linear
.fit-button.btn-default:hover:not(.active)
  color #58666e
  background-color #edf1f2
  border-color #ccd8da
.fit-button.btn-default:focus:not(.active), .fit-button.btn-default.focus:not(.active)
  color #58666e
  background-color #edf1f2
  border-color #ccd8da
.fit-button.btn-default:active, .fit-button.btn-default.active
  color #58666e
  border-color #ccd8da
  background-image none
  box-shadow inset 0 3px 5px rgba(0, 0, 0, 0.125)
.fit-button.btn-default.disabled:focus, .fit-button.btn-default.disabled.focus, .fit-button.btn-default:disabled:focus, .fit-button.btn-default:disabled.focus
  background-color #fcfdfd
  border-color #dee5e7
.fit-button.btn-default.disabled:hover, .fit-button.btn-default:disabled:hover
  background-color #fcfdfd
  border-color #dee5e7
.fit-button.btn-default.btn-bg
  border-color rgba(0, 0, 0, 0.1)
  background-clip padding-box

.fit-button.btn-primary
  color #fff
  background-color #7266ba
  border-color #7266ba
.fit-button.btn-primary .taint
  display block
  position absolute
  background rgba(255, 255, 255, 0.45)
  border-radius 100%
  -webkit-transform scale(0)
  transform scale(0)
.fit-button.btn-primary .taint.drop
  -webkit-animation fit-button-ripple 0.65s linear
  animation fit-button-ripple 0.65s linear
.fit-button.btn-primary:hover:not(.active)
  color #fff
  background-color #8c82c7
  border-color #8f86c8
.fit-button.btn-primaryfocus:not(.active), .fit-button.btn-primary.focus:not(.active)
  color #fff
  background-color #8c82c7
  border-color #8f86c8
.fit-button.btn-primary:active, .fit-button.btn-primary.active
  color #fff
  border-color #8f86c8
  background-image none
  box-shadow inset 0 3px 5px rgba(0, 0, 0, 0.125)
.fit-button.btn-primary.disabled:focus, .fit-button.btn-primary.disabled.focus, .fit-button.btn-primarydisabled:focus, .fit-button.btn-primary:disabled.focus
  background-color #7266ba
  border-color #7266ba
.fit-button.btn-primary.disabled:hover, .fit-button.btn-primary:disabled:hover
  background-color #7266ba
  border-color #7266ba

.fit-button.btn-success
  color #fff
  background-color #27c24c
  border-color #27c24c
.fit-button.btn-success .taint
  display block
  position absolute
  background rgba(255, 255, 255, 0.45)
  border-radius 100%
  -webkit-transform scale(0)
  transform scale(0)
.fit-button.btn-success .taint.drop
  -webkit-animation fit-button-ripple 0.65s linear
  animation fit-button-ripple 0.65s linear
.fit-button.btn-success:hover:not(.active)
  color #fff
  background-color #3ad760
  border-color #3fd863
.fit-button.btn-successfocus:not(.active), .fit-button.btn-success.focus:not(.active)
  color #fff
  background-color #3ad760
  border-color #3fd863
.fit-button.btn-success:active, .fit-button.btn-success.active
  color #fff
  border-color #3fd863
  background-image none
  box-shadow inset 0 3px 5px rgba(0, 0, 0, 0.125)
.fit-button.btn-success.disabled:focus, .fit-button.btn-success.disabled.focus, .fit-button.btn-success:disabled:focus, .fit-button.btn-success:disabled.focus
  background-color #27c24c
  border-color #27c24c
.fit-button.btn-success.disabled:hover, .fit-button.btn-success:disabled:hover
  background-color #27c24c
  border-color #27c24c

.fit-button.btn-info
  color #fff
  background-color #23b7e5
  border-color #23b7e5
.fit-button.btn-info .taint
  display block
  position absolute
  background rgba(255, 255, 255, 0.45)
  border-radius 100%
  -webkit-transform scale(0)
  transform scale(0)
.fit-button.btn-info .taint.drop
  -webkit-animation fit-button-ripple 0.65s linear
  animation fit-button-ripple 0.65s linear
.fit-button.btn-info:hover:not(.active)
  color #fff
  background-color #47c3e9
  border-color #4cc4ea
.fit-button.btn-info:focus:not(.active), .fit-button.btn-info.focus:not(.active)
  color #fff
  background-color #47c3e9
  border-color #4cc4ea
.fit-button.btn-info:active, .fit-button.btn-info.active
  color #fff
  border-color #4cc4ea
  background-image none
  box-shadow inset 0 3px 5px rgba(0, 0, 0, 0.125)
.fit-button.btn-info.disabled:focus, .fit-button.btn-info.disabled.focus, .fit-button.btn-info:disabled:focus, .fit-button.btn-info:disabled.focus
  background-color #23b7e5
  border-color #23b7e5
.fit-button.btn-info.disabled:hover, .fit-button.btn-info:disabled:hover
  background-color #23b7e5
  border-color #23b7e5

.fit-button.btn-warning
  color #fff
  background-color #fad733
  border-color #fad733
.fit-button.btn-warning .taint
  display block
  position absolute
  background rgba(255, 255, 255, 0.45)
  border-radius 100%
  -webkit-transform scale(0)
  transform scale(0)
.fit-button.btn-warning .taint.drop
  -webkit-animation fit-button-ripple 0.65s linear
  animation fit-button-ripple 0.65s linear
.fit-button.btn-warning:hover:not(.active)
  color #fff
  background-color #fbdf5b
  border-color #fbe060
.fit-button.btn-warning:focus:not(.active), .fit-button.btn-warning.focus:not(.active)
  color #fff
  background-color #fbdf5b
  border-color #fbe060
.fit-button.btn-warning:active, .fit-button.btn-warning.active
  color #fff
  border-color #fbe060
  background-image none
  box-shadow inset 0 3px 5px rgba(0, 0, 0, 0.125)
.fit-button.btn-warning.disabled:focus, .fit-button.btn-warning.disabled.focus, .fit-button.btn-warning:disabled:focus, .fit-button.btn-warning:disabled.focus
  background-color #fad733
  border-color #fad733
.fit-button.btn-warning.disabled:hover, .fit-button.btn-warning:disabled:hover
  background-color #fad733
  border-color #fad733
.fit-button.btn-warning:hover, .fit-button.btn-warning:active, .fit-button.btn-warning.active
  color #ffffff !important
  background-color #f9d21a
  border-color #f9cf0b

.fit-button.btn-danger
  color #fff
  background-color #f05050
  border-color #f05050
.fit-button.btn-danger .taint
  display block
  position absolute
  background rgba(255, 255, 255, 0.45)
  border-radius 100%
  -webkit-transform scale(0)
  transform scale(0)
.fit-button.btn-danger .taint.drop
  -webkit-animation fit-button-ripple 0.65s linear
  animation fit-button-ripple 0.65s linear
.fit-button.btn-danger:hover:not(.active)
  color #fff
  background-color #f37676
  border-color #f47a7a
.fit-button.btn-danger:focus:not(.active), .fit-button.btn-danger.focus:not(.active)
  color #fff
  background-color #f37676
  border-color #f47a7a
.fit-button.btn-danger:active, .fit-button.btn-danger.active
  color #fff
  border-color #f47a7a
  background-image none
  box-shadow inset 0 3px 5px rgba(0, 0, 0, 0.125)
.fit-button.btn-danger.disabled:focus, .fit-button.btn-danger.disabled.focus, .fit-button.btn-danger:disabled:focus, .fit-button.btn-danger:disabled.focus
  background-color #f05050
  border-color #f05050
.fit-button.btn-danger.disabled:hover, .fit-button.btn-danger:disabled:hover
  background-color #f05050
  border-color #f05050

.fit-button.btn-dark
  color #fff
  background-color #3a3f51
  border-color #3a3f51
.fit-button.btn-dark .taint
  display block
  position absolute
  background rgba(255, 255, 255, 0.45)
  border-radius 100%
  -webkit-transform scale(0)
  transform scale(0)
.fit-button.btn-dark .taint.drop
  -webkit-animation fit-button-ripple 0.65s linear
  animation fit-button-ripple 0.65s linear
.fit-button.btn-dark:hover:not(.active)
  color #fff
  background-color #4b5169
  border-color #4d546c
.fit-button.btn-dark:focus:not(.active), .fit-button.btn-dark.focus:not(.active)
  color #fff
  background-color #4b5169
  border-color #4d546c
.fit-button.btn-dark:active, .fit-button.btn-dark.active
  color #fff
  border-color #4d546c
  background-image none
  box-shadow inset 0 3px 5px rgba(0, 0, 0, 0.125)
.fit-button.btn-dark.disabled:focus, .fit-button.btn-dark.disabled.focus, .fit-button.btn-dark:disabled:focus, .fit-button.btn-dark:disabled.focus
  background-color #3a3f51
  border-color #3a3f51
.fit-button.btn-dark.disabled:hover, .fit-button.btn-dark:disabled:hover
  background-color #3a3f51
  border-color #3a3f51

.fit-button.btn-black
  color #fff
  background-color #1c2b36
  border-color #1c2b36
.fit-button.btn-black .taint
  display block
  position absolute
  background rgba(255, 255, 255, 0.45)
  border-radius 100%
  -webkit-transform scale(0)
  transform scale(0)
.fit-button.btn-black .taint.drop
  -webkit-animation fit-button-ripple 0.65s linear
  animation fit-button-ripple 0.65s linear
.fit-button.btn-black:hover:not(.active)
  color #fff
  background-color #2a4051
  border-color #2c4354
.fit-button.btn-black:focus:not(.active), .fit-button.btn-black.focus:not(.active)
  color #fff
  background-color #2a4051
  border-color #2c4354
.fit-button.btn-black:active, .fit-button.btn-black.active
  color #fff
  border-color #2c4354
  background-image none
  box-shadow inset 0 3px 5px rgba(0, 0, 0, 0.125)
.fit-button.btn-black.disabled:focus, .fit-button.btn-black.disabled.focus, .fit-button.btn-black:disabled:focus, .fit-button.btn-black:disabled.focus
  background-color #1c2b36
  border-color #1c2b36
.fit-button.btn-black.disabled:hover, .fit-button.btn-black:disabled:hover
  background-color #1c2b36
  border-color #1c2b36

.fit-button.btn-secondary
  color #58666e
  background-color white
  border-color white
.fit-button.btn-secondary .taint
  display block
  position absolute
  background rgba(0, 0, 0, 0.1)
  border-radius 100%
  -webkit-transform scale(0)
  transform scale(0)
.fit-button.btn-secondary .taint.drop
  -webkit-animation fit-button-ripple 0.65s linear
  animation fit-button-ripple 0.65s linear
.fit-button.btn-secondary:hover:not(.active)
  color #58666e
  background-color #f2f2f2
  border-color #f0f0f0
.fit-button.btn-secondary:focus:not(.active), .fit-button.btn-secondary.focus:not(.active)
  color #58666e
  background-color #f2f2f2
  border-color #f0f0f0
.fit-button.btn-secondary:active, .fit-button.btn-secondary.active
  color #58666e
  border-color #f0f0f0
  background-image none
  box-shadow inset 0 3px 5px rgba(0, 0, 0, 0.125)
.fit-button.btn-secondary.disabled:focus, .fit-button.btn-secondary.disabled.focus, .fit-button.btn-secondary:disabled:focus, .fit-button.btn-secondary:disabled.focus
  background-color white
  border-color white
.fit-button.btn-secondary.disabled:hover, .fit-button.btn-secondary:disabled:hover
  background-color white
  border-color white
.fit-button.btn-secondary:hover:not(.active)
  border 1px solid #ccc

.fit-button.btn-icon
  padding 0 !important
  text-align center
  width 34px
  height 34px
.fit-button.btn-icon i
  top -1px
  position relative
  line-height 34px

.fit-button.btn-sm
  line-height 1.5rem

.fit-button.btn-rounded
  border-radius 50px
  padding-left 15px
  padding-right 15px
.fit-button.btn-rounded.btn-lg
  padding-left 25px
  padding-right 25px

.fit-button.btn > i.pull-left, .fit-button.btn > i.pull-right
  line-height 2.5rem

.fit-button.btn-block
  padding-left 12px
  padding-right 12px

.fit-button.btn-group-vertical > .btn:first-child:not(last-child)
  border-top-right-radius 2px

.fit-button.btn-group-vertical > .btn:last-child:not(first-child)
  border-bottom-left-radius 2px

.fit-button.btn-addon i
  display -webkit-box
  display -webkit-flex
  display -ms-flexbox
  display flex
  -webkit-box-align center
  -webkit-align-items center
  -ms-flex-align center
  align-items center
  -webkit-box-pack center
  -webkit-justify-content center
  -ms-flex-pack center
  justify-content center
  background-color rgba(0, 0, 0, 0.1)
  width 30px
  position relative
  border-radius 2px 0 0 2px

.fit-button.btn-addon.btn-sm i
  width 30px

.fit-button.btn-addon.btn-lg i
  width 50px

.fit-button.btn-addon.btn-xs i
  width 30px

.fit-button.btn-addon.btn-sm i
  width 25px

.fit-button.btn-addon.btn-default i
  background-color transparent
  border-right 1px solid #dee5e7

.fit-button.btn-groups .btn
  margin-bottom 5px

@-webkit-keyframes fit-button-ripple
  0%
    opacity 1
    -webkit-transform scale(0)
    transform scale(0)
  100%
    opacity 0
    -webkit-transform scale(2.5)
    transform scale(2.5)

@keyframes fit-button-ripple
  0%
    opacity 1
    -webkit-transform scale(0)
    transform scale(0)
  100%
    opacity 0
    -webkit-transform scale(2.5)
    transform scale(2.5)
</style>
