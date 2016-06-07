<template lang="jade">
div(:class="classes")
  slot
</template>

<script>
export default {
  props: ['vertical'],
  computed: {
    classes () {
      return {
        'btn-group': !this.vertical,
        'btn-group-vertical': this.vertical
      }
    }
  }
}
</script>

<style lang="stylus">
$btn-border-radius-base= 4px;

&.btn-group,
&.btn-group-vertical
    position: relative;
    display: inline-block;
    vertical-align: middle;
    > .btn
        position: relative;
        float: left;
        // Bring the "active" button to the front
        &:hover,
        &:focus,
        &:active,
        &.active
            z-index: 2;




// Prevent double borders when buttons are next to each other
&.btn-group
    .btn + .btn,
    .btn + .btn-group,
    .btn-group + .btn,
    .btn-group + .btn-group
        margin-left: -1px;



&.btn-group > .btn:not(:first-child):not(:last-child):not(.dropdown-toggle)
    border-radius: 0;


// Set corners individual because sometimes a single button can be in a .btn-group and we need :first-child and :last-child to both match
&.btn-group > .btn:first-child
    margin-left: 0;
    &:not(:last-child):not(.dropdown-toggle)
        border-bottom-right-radius: 0;
        border-top-right-radius: 0;



// Need .dropdown-toggle since :last-child doesn't apply, given that a .dropdown-menu is used immediately after it
&.btn-group > .btn:last-child:not(:first-child),
&.btn-group > .dropdown-toggle:not(:first-child)
    border-bottom-left-radius: 0;
    border-top-left-radius: 0;


// Custom edits for including btn-groups within btn-groups (useful for including dropdown buttons within a btn-group)
&.btn-group > .btn-group
    float: left;


&.btn-group > .btn-group:not(:first-child):not(:last-child) > .btn
    border-radius: 0;


&.btn-group > .btn-group:first-child:not(:last-child)
    > .btn:last-child,
    > .dropdown-toggle
        border-bottom-right-radius: 0;
        border-top-right-radius: 0;



&.btn-group > .btn-group:last-child:not(:first-child) > .btn:first-child
    border-bottom-left-radius: 0;
    border-top-left-radius: 0;


// On active and open, don't show outline
&.btn-group .dropdown-toggle:active,
&.btn-group.open .dropdown-toggle
    outline: 0;


// Vertical button groups
// ----------------------

&.btn-group-vertical
    > .btn,
    > .btn-group,
    > .btn-group > .btn
        display: block;
        float: none;
        width: 100%;
        max-width: 100%;


    > .btn + .btn,
    > .btn + .btn-group,
    > .btn-group + .btn,
    > .btn-group + .btn-group
        margin-top: -1px;
        margin-left: 0;



&.btn-group-vertical > .btn
    &:not(:first-child):not(:last-child)
        border-radius: 0;

    &:first-child:not(:last-child)
        border-radius: $btn-border-radius-base $btn-border-radius-base 0 0;

    &:last-child:not(:first-child)
        border-radius: 0 0 $btn-border-radius-base $btn-border-radius-base;



&.btn-group-vertical > .btn-group:not(:first-child):not(:last-child) > .btn
    border-radius: 0;


&.btn-group-vertical > .btn-group:first-child:not(:last-child)
    > .btn:last-child,
    > .dropdown-toggle
        border-bottom-left-radius: 0;
        border-bottom-right-radius: 0;



&.btn-group-vertical > .btn-group:last-child:not(:first-child) > .btn:first-child
    border-top-left-radius: 0;
    border-top-right-radius: 0;


</style>
