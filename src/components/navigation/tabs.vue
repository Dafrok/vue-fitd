<template lang="jade">
div.fit-tabs
  div.title-container(v-el:"title-container")
    div.move-bar(:class="moveBarClassNames", :style="moveBarStyle")
    div.title-item(v-for="tab of tabs", @click="changeTab($index)", v-text="tab.titleContent", :class="{active: activeKey == $index, [`title-item-${$index}`]: true}")
  div.content-container
    slot
</template>
<script>
import Vue from 'vue'
export default {
  props: ['default-active-key'],
  data () {
    return {
      activeKey: this.defaultActiveKey,
      moveBarStyle: {},
      isForward: null
    }
  },
  ready () {
    Vue.nextTick(() => this.changeTab(this.activeKey))
  },
  computed: {
    tabs () {
      const result = []
      for (const child of this.$children) {
        if (child.$options.name === 'tab-panel') {
          result.push({titleContent: child._props.tab.raw})
        }
      }
      return result
    },
    moveBarClassNames () {
      return {
        'forward': this.isForward,
        'backward': !this.isForward
      }
    }
  },
  methods: {
    changeTab (index) {
      const previousTitleIndex = +this.activeKey
      const $titleContainer = this.$els.titleContainer
      const $titleItem = $titleContainer.querySelector(`.title-item-${index}`)
      const currentLeft = $titleItem.offsetLeft
      this.activeKey = index
      this.isForward = index > previousTitleIndex
      this.moveBarStyle = {
        left: currentLeft + 'px',
        right: parseFloat(global.getComputedStyle($titleContainer).width) - +currentLeft - parseFloat(global.getComputedStyle($titleItem).width) - 20 + 'px'
      }
      if (index !== previousTitleIndex) {
        this.$emit('change')
        this.activeKey = index
      }
    }
  }
}
</script>
<style scoped>
.fit-tabs .title-container {
  font-size: 14px;
  font-family: "Source Sans Pro", "Helvetica Neue", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  color: #333;
  box-sizing: border-box;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  position: relative; }
  .fit-tabs .title-container .title-item {
    cursor: pointer;
    padding: 5px 10px 10px 10px; }
    .fit-tabs .title-container .title-item.active {
      color: #23b7e5;
      cursor: default; }

.fit-tabs .content-container {
  padding: 0 10px; }

.fit-tabs .move-bar {
  z-index: 1;
  position: absolute;
  left: 0;
  bottom: 0;
  box-sizing: border-box;
  height: 2px;
  background-color: #2db7f5;
  -webkit-transform: scaleX(1);
          transform: scaleX(1);
  -webkit-transform-origin: 0 0;
          transform-origin: 0 0; }
  .fit-tabs .move-bar.forward {
    -webkit-transition: right 0.3s cubic-bezier(0.645, 0.045, 0.355, 1), left 0.3s cubic-bezier(0.645, 0.045, 0.355, 1) 0.09s;
    transition: right 0.3s cubic-bezier(0.645, 0.045, 0.355, 1), left 0.3s cubic-bezier(0.645, 0.045, 0.355, 1) 0.09s; }
  .fit-tabs .move-bar.backward {
    -webkit-transition: right 0.3s cubic-bezier(0.65, 0.05, 0.36, 1) 0.09s, left 0.3s cubic-bezier(0.645, 0.045, 0.355, 1);
    transition: right 0.3s cubic-bezier(0.65, 0.05, 0.36, 1) 0.09s, left 0.3s cubic-bezier(0.645, 0.045, 0.355, 1); }

.fit-tabs.retro .title-container {
  border-bottom: 1px solid #ddd;
  background: whitesmoke;
  padding: 5px 5px 0 10px;
  height: 36px; }
  .fit-tabs.retro .title-container .title-item {
    margin-bottom: -1px;
    font-size: 12px;
    color: #666;
    border: 1px solid transparent;
    border-bottom: none;
    padding: 0 10px;
    height: 30px;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
        -ms-flex-direction: column;
            flex-direction: column;
    position: relative; }
    .fit-tabs.retro .title-container .title-item.active {
      background: white;
      border-color: #ddd;
      color: #666;
      border-top-left-radius: 10px;
      border-top-right-radius: 10px; }

.fit-tabs.retro .content-container {
  padding: 0;
  -webkit-box-flex: 1;
      -ms-flex-positive: 1;
          flex-grow: 1;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
      -ms-flex-direction: column;
          flex-direction: column;
  height: 0; }

.fit-tabs.retro .tab-panel {
  -webkit-box-flex: 1;
      -ms-flex-positive: 1;
          flex-grow: 1;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
      -ms-flex-direction: column;
          flex-direction: column; }

.fit-tabs.retro .move-bar {
  background: transparent; }

.fit-tabs.retro .center-text {
  -webkit-box-flex: 1;
      -ms-flex-positive: 1;
          flex-grow: 1;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
      -ms-flex-pack: center;
          justify-content: center;
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center; }

.fit-tabs.retro .tab-bar-content {
  position: relative;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
      -ms-flex-pack: center;
          justify-content: center;
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center;
  -webkit-box-flex: 1;
      -ms-flex-positive: 1;
          flex-grow: 1; }
  .fit-tabs.retro .tab-bar-content .tab-bar-left {
    position: absolute;
    left: -20px;
    width: 10px;
    height: 10px;
    overflow: hidden;
    bottom: 0; }
  .fit-tabs.retro .tab-bar-content .tab-bar-left-nav {
    width: 20px;
    height: 20px;
    margin-top: -10px;
    margin-left: -10px;
    background: -webkit-radial-gradient(transparent 60%, #ccc 70%, white 70%);
    background: radial-gradient(transparent 60%, #ccc 70%, white 70%); }
  .fit-tabs.retro .tab-bar-content .tab-bar-right {
    position: absolute;
    right: -20px;
    width: 10px;
    height: 10px;
    overflow: hidden;
    bottom: 0; }
  .fit-tabs.retro .tab-bar-content .tab-bar-right-nav {
    width: 20px;
    height: 20px;
    margin-top: -10px;
    background: -webkit-radial-gradient(transparent 60%, #ccc 70%, white 70%);
    background: radial-gradient(transparent 60%, #ccc 70%, white 70%); }
</style>
