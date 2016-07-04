<template lang="jade">
div(class="fit-input")
  input(required, @change.stop="inputChange", class="input", :placeholder="placeholder", v-model="value")
  div.right-addon
      slot(name="rightRender")
  slot(name="innerRender")
  span(class="highlight", v-if="highlight")
  span(class="bottom-bar")
  label(:class="`label ${direction}`")
    span(v-text="label")
    span(class="label-error")
</template>

<script>
export default {
  props: ['value', 'label', 'direction', 'highlight', 'placeholder'],
  data () {
    return {
    }
  },
  methods: {
    inputChange (e) {
      this.$emit('change', e)
    }
  }
}
</script>

<style lang="stylus" scoped>
.fit-input {
  font-size: 14px;
  font-family: "Source Sans Pro", "Helvetica Neue", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  color: #333;
  box-sizing: border-box;
  position: relative;
  margin-top: 20px;
  background: white; }

.fit-input .input {
  font-size: 14px;
  padding: 10px 10px 10px 5px;
  display: block;
  width: 100%;
  border: none;
  border-bottom: 1px solid #ccc;
  box-sizing: border-box;
  color: #333; }
  .fit-input .input.center {
    text-align: center; }
  .fit-input .input:focus {
    outline: none; }
  .fit-input .input:disabled {
    border-bottom: 1px dotted #ccc; }
  .fit-input .input:not(:focus)::-webkit-input-placeholder {
    -webkit-transition: opacify .3s;
    transition: opacify .3s;
    opacity: 0; }
  .fit-input .input:not(:focus):-moz-placeholder {
    /* Firefox 18- */
    -webkit-transition: opacify .3s;
    transition: opacify .3s;
    opacity: 0; }
  .fit-input .input:not(:focus)::-moz-placeholder {
    /* Firefox 19+ */
    -webkit-transition: opacify .3s;
    transition: opacify .3s;
    opacity: 0; }
  .fit-input .input:not(:focus):-ms-input-placeholder {
    -webkit-transition: opacify .3s;
    transition: opacify .3s;
    opacity: 0; }
  .fit-input .input:not(:focus).no-label::-webkit-input-placeholder {
    opacity: 1; }
  .fit-input .input:not(:focus).no-label:-moz-placeholder {
    /* Firefox 18- */
    opacity: 1; }
  .fit-input .input:not(:focus).no-label::-moz-placeholder {
    /* Firefox 19+ */
    opacity: 1; }
  .fit-input .input:not(:focus).no-label:-ms-input-placeholder {
    opacity: 1; }

.fit-input .label {
  color: #999;
  font-size: 14px;
  font-weight: normal;
  position: absolute;
  pointer-events: none;
  left: 5px;
  top: 10px;
  transition: 0.2s ease all;
  -moz-transition: 0.2s ease all;
  -webkit-transition: 0.2s ease all; }
  .fit-input .label.center {
    width: 100%;
    text-align: center; }
  .fit-input .label .label-error {
    color: #f50;
    margin-left: 10px; }

.fit-input .input:focus ~ .label, .fit-input .input:valid ~ .label {
  top: -10px;
  font-size: 12px;
  font-weight: bold;
  color: #7266ba; }

.fit-input .input:valid:not(:focus) ~ .label {
  color: #999; }

.fit-input .bottom-bar {
  position: relative;
  display: block;
  width: 100%; }
  .fit-input .bottom-bar:before, .fit-input .bottom-bar:after {
    content: '';
    height: 2px;
    width: 0;
    bottom: 0;
    position: absolute;
    background: #7266ba;
    transition: 0.2s ease all;
    -moz-transition: 0.2s ease all;
    -webkit-transition: 0.2s ease all; }
  .fit-input .bottom-bar:before {
    left: 50%; }
  .fit-input .bottom-bar:after {
    right: 50%; }
  .fit-input .bottom-bar.bottom-bar-error:before, .fit-input .bottom-bar.bottom-bar-error:after {
    width: 50%;
    background: #f50; }

.fit-input .input:focus ~ .bottom-bar:before, .fit-input .input:focus ~ .bottom-bar:after {
  width: 50%; }

.fit-input .highlight {
  position: absolute;
  height: 60%;
  width: 100px;
  top: 25%;
  left: 0;
  pointer-events: none;
  opacity: 0.5; }

.fit-input .input:focus ~ .highlight {
  -webkit-animation: inputHighlighter 0.3s ease;
  animation: inputHighlighter 0.3s ease; }

.fit-input .right-addon {
  position: absolute;
  right: 0;
  top: 0;
  height: 38px;
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -webkit-justify-content: center;
      -ms-flex-pack: center;
          justify-content: center;
  -webkit-box-align: center;
  -webkit-align-items: center;
      -ms-flex-align: center;
          align-items: center; }

@-webkit-keyframes inputHighlighter {
  from {
    background: #5264AE; }
  to {
    width: 0;
    background: transparent; } }

@keyframes inputHighlighter {
  from {
    background: #5264AE; }
  to {
    width: 0;
    background: transparent; } }
</style>
