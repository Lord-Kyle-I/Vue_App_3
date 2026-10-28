<script>
import {Tooltip} from "bootstrap";

export default {
  name: "DataTooltip",
  props: {
    text: {type: String, required: true},
    placement: {type: String, required: true}
  },
  mounted() {
    console.log('here')
    const bsTooltip = new Tooltip(this.$refs.tooltip)
  },
}
</script>

<template>
  <div ref="tooltip" :data-bs-placement="placement" :data-bs-title="text">
    <slot></slot>
  </div>
</template>

<style scoped>

</style>