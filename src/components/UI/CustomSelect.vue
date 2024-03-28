<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  name: "CustomSelect",
  props: {
    name:{
      type: String,
      required: false
    },
    disabled:{
      type: Boolean,
      required: false
    },
    placeholder:{
      type: String,
      required: false
    },
    required: {
      type: Boolean,
      required: false,
      default: false
    },
  },
  data(){
    return {
      model: '',
      error: '',
      hasError: false,
    }
  },
})
</script>

<template>
  <select
      v-model="model"
      :name="name"
      :disabled="disabled"
      class="form-select"
      ref="root"
  >
    <!-- DEFAULT VALUE-->
    <slot />

  </select>
  <span role="alert" class="text-red" v-if="hasError">
      {{ error }}
  </span>
</template>

<style scoped lang="sass">
select
  width: 100%
  padding: 12px 0 12px 15px
  border: 1px solid #DCDFE6
  color: #606266
  border-radius: 4px
  transition: 0.2s ease
  text-overflow: ellipsis
  &:focus
    border: 1px solid #17505B
    outline: none

</style>
