<template lang="jade">
div(:class="classes")
  slot
</template>

<script>
export default {
  props: ['span', 'order', 'offset', 'push', 'pull'],
  computed: {
    classes () {
      return {
        'col': true,
        'fit-layout-col': true,
        ['col-' + this.span]: this.span,
        ['col-order-' + this.order]: this.order,
        ['col-offset-' + this.offset]: this.offset,
        ['col-push-' + this.push]: this.push,
        ['col-pull-' + this.pull]: this.pull
      }
    }
  }
}
</script>

<style lang="stylus">
.fit-layout-col
  box-sizing border-box

.fit-layout-col.col
  position relative
  display block
  float left
  -webkit-box-flex 0
  -webkit-flex 0 0 auto
  -ms-flex 0 0 auto
  flex 0 0 auto

.fit-layout-col.col-1, .fit-layout-col.col-2, .fit-layout-col.col-3, .fit-layout-col.col-4, .fit-layout-col.col-5, .fit-layout-col.col-6, .fit-layout-col.col-7, .fit-layout-col.col-8, .fit-layout-col.col-9, .fit-layout-col.col-10, .fit-layout-col.col-11, .fit-layout-col.col-12, .fit-layout-col.col-13, .fit-layout-col.col-14, .fit-layout-col.col-15, .fit-layout-col.col-16, .fit-layout-col.col-17, .fit-layout-col.col-18, .fit-layout-col.col-19, .fit-layout-col.col-20, .fit-layout-col.col-21, .fit-layout-col.col-22, .fit-layout-col.col-23, .fit-layout-col.col-24
  position relative
  display block
  float left
  -webkit-box-flex 0
  -webkit-flex 0 0 auto
  -ms-flex 0 0 auto
  flex 0 0 auto
  padding-left 0
  padding-right 0

.fit-layout-col.col-24
  width 100%

.fit-layout-col.col-push-24
  left 100%

.fit-layout-col.col-pull-24
  right 100%

.fit-layout-col.col-offset-24
  margin-left 100%

.fit-layout-col.col-order-24
  -webkit-box-ordinal-group 25
  -webkit-order 24
  -ms-flex-order 24
  order 24

.fit-layout-col.col-23
  width 95.83333333%

.fit-layout-col.col-push-23
  left 95.83333333%

.fit-layout-col.col-pull-23
  right 95.83333333%

.fit-layout-col.col-offset-23
  margin-left 95.83333333%

.fit-layout-col.col-order-23
  -webkit-box-ordinal-group 24
  -webkit-order 23
  -ms-flex-order 23
  order 23

.fit-layout-col.col-22
  width 91.66666667%

.fit-layout-col.col-push-22
  left 91.66666667%

.fit-layout-col.col-pull-22
  right 91.66666667%

.fit-layout-col.col-offset-22
  margin-left 91.66666667%

.fit-layout-col.col-order-22
  -webkit-box-ordinal-group 23
  -webkit-order 22
  -ms-flex-order 22
  order 22

.fit-layout-col.col-21
  width 87.5%

.fit-layout-col.col-push-21
  left 87.5%

.fit-layout-col.col-pull-21
  right 87.5%

.fit-layout-col.col-offset-21
  margin-left 87.5%

.fit-layout-col.col-order-21
  -webkit-box-ordinal-group 22
  -webkit-order 21
  -ms-flex-order 21
  order 21

.fit-layout-col.col-20
  width 83.33333333%

.fit-layout-col.col-push-20
  left 83.33333333%

.fit-layout-col.col-pull-20
  right 83.33333333%

.fit-layout-col.col-offset-20
  margin-left 83.33333333%

.fit-layout-col.col-order-20
  -webkit-box-ordinal-group 21
  -webkit-order 20
  -ms-flex-order 20
  order 20

.fit-layout-col.col-19
  width 79.16666667%

.fit-layout-col.col-push-19
  left 79.16666667%

.fit-layout-col.col-pull-19
  right 79.16666667%

.fit-layout-col.col-offset-19
  margin-left 79.16666667%

.fit-layout-col.col-order-19
  -webkit-box-ordinal-group 20
  -webkit-order 19
  -ms-flex-order 19
  order 19

.fit-layout-col.col-18
  width 75%

.fit-layout-col.col-push-18
  left 75%

.fit-layout-col.col-pull-18
  right 75%

.fit-layout-col.col-offset-18
  margin-left 75%

.fit-layout-col.col-order-18
  -webkit-box-ordinal-group 19
  -webkit-order 18
  -ms-flex-order 18
  order 18

.fit-layout-col.col-17
  width 70.83333333%

.fit-layout-col.col-push-17
  left 70.83333333%

.fit-layout-col.col-pull-17
  right 70.83333333%

.fit-layout-col.col-offset-17
  margin-left 70.83333333%

.fit-layout-col.col-order-17
  -webkit-box-ordinal-group 18
  -webkit-order 17
  -ms-flex-order 17
  order 17

.fit-layout-col.col-16
  width 66.66666667%

.fit-layout-col.col-push-16
  left 66.66666667%

.fit-layout-col.col-pull-16
  right 66.66666667%

.fit-layout-col.col-offset-16
  margin-left 66.66666667%

.fit-layout-col.col-order-16
  -webkit-box-ordinal-group 17
  -webkit-order 16
  -ms-flex-order 16
  order 16

.fit-layout-col.col-15
  width 62.5%

.fit-layout-col.col-push-15
  left 62.5%

.fit-layout-col.col-pull-15
  right 62.5%

.fit-layout-col.col-offset-15
  margin-left 62.5%

.fit-layout-col.col-order-15
  -webkit-box-ordinal-group 16
  -webkit-order 15
  -ms-flex-order 15
  order 15

.fit-layout-col.col-14
  width 58.33333333%

.fit-layout-col.col-push-14
  left 58.33333333%

.fit-layout-col.col-pull-14
  right 58.33333333%

.fit-layout-col.col-offset-14
  margin-left 58.33333333%

.fit-layout-col.col-order-14
  -webkit-box-ordinal-group 15
  -webkit-order 14
  -ms-flex-order 14
  order 14

.fit-layout-col.col-13
  width 54.16666667%

.fit-layout-col.col-push-13
  left 54.16666667%

.fit-layout-col.col-pull-13
  right 54.16666667%

.fit-layout-col.col-offset-13
  margin-left 54.16666667%

.fit-layout-col.col-order-13
  -webkit-box-ordinal-group 14
  -webkit-order 13
  -ms-flex-order 13
  order 13

.fit-layout-col.col-12
  width 50%

.fit-layout-col.col-push-12
  left 50%

.fit-layout-col.col-pull-12
  right 50%

.fit-layout-col.col-offset-12
  margin-left 50%

.fit-layout-col.col-order-12
  -webkit-box-ordinal-group 13
  -webkit-order 12
  -ms-flex-order 12
  order 12

.fit-layout-col.col-11
  width 45.83333333%

.fit-layout-col.col-push-11
  left 45.83333333%

.fit-layout-col.col-pull-11
  right 45.83333333%

.fit-layout-col.col-offset-11
  margin-left 45.83333333%

.fit-layout-col.col-order-11
  -webkit-box-ordinal-group 12
  -webkit-order 11
  -ms-flex-order 11
  order 11

.fit-layout-col.col-10
  width 41.66666667%

.fit-layout-col.col-push-10
  left 41.66666667%

.fit-layout-col.col-pull-10
  right 41.66666667%

.fit-layout-col.col-offset-10
  margin-left 41.66666667%

.fit-layout-col.col-order-10
  -webkit-box-ordinal-group 11
  -webkit-order 10
  -ms-flex-order 10
  order 10

.fit-layout-col.col-9
  width 37.5%

.fit-layout-col.col-push-9
  left 37.5%

.fit-layout-col.col-pull-9
  right 37.5%

.fit-layout-col.col-offset-9
  margin-left 37.5%

.fit-layout-col.col-order-9
  -webkit-box-ordinal-group 10
  -webkit-order 9
  -ms-flex-order 9
  order 9

.fit-layout-col.col-8
  width 33.33333333%

.fit-layout-col.col-push-8
  left 33.33333333%

.fit-layout-col.col-pull-8
  right 33.33333333%

.fit-layout-col.col-offset-8
  margin-left 33.33333333%

.fit-layout-col.col-order-8
  -webkit-box-ordinal-group 9
  -webkit-order 8
  -ms-flex-order 8
  order 8

.fit-layout-col.col-7
  width 29.16666667%

.fit-layout-col.col-push-7
  left 29.16666667%

.fit-layout-col.col-pull-7
  right 29.16666667%

.fit-layout-col.col-offset-7
  margin-left 29.16666667%

.fit-layout-col.col-order-7
  -webkit-box-ordinal-group 8
  -webkit-order 7
  -ms-flex-order 7
  order 7

.fit-layout-col.col-6
  width 25%

.fit-layout-col.col-push-6
  left 25%

.fit-layout-col.col-pull-6
  right 25%

.fit-layout-col.col-offset-6
  margin-left 25%

.fit-layout-col.col-order-6
  -webkit-box-ordinal-group 7
  -webkit-order 6
  -ms-flex-order 6
  order 6

.fit-layout-col.col-5
  width 20.83333333%

.fit-layout-col.col-push-5
  left 20.83333333%

.fit-layout-col.col-pull-5
  right 20.83333333%

.fit-layout-col.col-offset-5
  margin-left 20.83333333%

.fit-layout-col.col-order-5
  -webkit-box-ordinal-group 6
  -webkit-order 5
  -ms-flex-order 5
  order 5

.fit-layout-col.col-4
  width 16.66666667%

.fit-layout-col.col-push-4
  left 16.66666667%

.fit-layout-col.col-pull-4
  right 16.66666667%

.fit-layout-col.col-offset-4
  margin-left 16.66666667%

.fit-layout-col.col-order-4
  -webkit-box-ordinal-group 5
  -webkit-order 4
  -ms-flex-order 4
  order 4

.fit-layout-col.col-3
  width 12.5%

.fit-layout-col.col-push-3
  left 12.5%

.fit-layout-col.col-pull-3
  right 12.5%

.fit-layout-col.col-offset-3
  margin-left 12.5%

.fit-layout-col.col-order-3
  -webkit-box-ordinal-group 4
  -webkit-order 3
  -ms-flex-order 3
  order 3

.fit-layout-col.col-2
  width 8.33333333%

.fit-layout-col.col-push-2
  left 8.33333333%

.fit-layout-col.col-pull-2
  right 8.33333333%

.fit-layout-col.col-offset-2
  margin-left 8.33333333%

.fit-layout-col.col-order-2
  -webkit-box-ordinal-group 3
  -webkit-order 2
  -ms-flex-order 2
  order 2

.fit-layout-col.col-1
  width 4.16666667%

.fit-layout-col.col-push-1
  left 4.16666667%

.fit-layout-col.col-pull-1
  right 4.16666667%

.fit-layout-col.col-offset-1
  margin-left 4.16666667%

.fit-layout-col.col-order-1
  -webkit-box-ordinal-group 2
  -webkit-order 1
  -ms-flex-order 1
  order 1

.fit-layout-col.col-push-0
  left auto

.fit-layout-col.col-pull-0
  right auto
</style>
