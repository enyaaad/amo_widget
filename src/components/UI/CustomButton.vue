<script lang="ts">
import {defineComponent} from 'vue'


export default defineComponent({
  name: "CustomButton",
  props: {
    name:{
      type: String,
      required: false
    },
    disabled:{
      type: Boolean,
      required: false
    },
    type:{
      type: String,
      required: false
    },
  },
})
</script>

<template>
  <button
      :type="type"
      class="font-header"
  >
    <slot/>
  </button>
</template>

<style scoped lang="sass">
button
  width: 100%
  color: white
  background-color: #17505B
  padding: 13px 0
  border: none
  border-radius: 4px
  font-size: 1em
  cursor: pointer
</style>
