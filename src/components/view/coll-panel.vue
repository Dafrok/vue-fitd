<template lang="jade">
div.fit-collapse-coll-panel
  div.panel-heading(@click="handleClick")
    i(:class="rightChevronClass", style="margin-right: 5px", v-text="header")
  div(:class="panelCollapseClass", :style="contentContainerStyle")
    div(data-fit-coll-content)
      slot
</template>

<script>
export default {
  props: ['default-value', 'header']
}
</script>

<style>
.fit-collapse-coll-panel {
  background-color: #fff;
  border: 1px solid #dee5e7;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05); }
  .fit-collapse-coll-panel.panel-default:not(:first-child) {
    border-top: none; }

.fit-collapse-coll-panel .panel-collapse {
  -webkit-transition: all .3s ease-in-out;
  transition: all .3s ease-in-out;
  overflow: hidden;
  height: 0; }

.fit-collapse-coll-panel .panel-heading {
  border-color: #edf1f2;
  padding: 10px;
  background-color: #f6f8f8;
  cursor: pointer; }

.fit-collapse-coll-panel .rotate-pre {
  -webkit-transition: all .3s;
  transition: all .3s; }
.fit-collapse-coll-panel .rotate-pre.rotate {
  -webkit-transform: rotate(90deg);
          transform: rotate(90deg); }
</style>
