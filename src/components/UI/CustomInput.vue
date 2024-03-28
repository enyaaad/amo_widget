<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  name: "CustomInput",
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
    hasError: {
      type: Boolean,
      required: true,
      default: false
    }
  },
  data(){
    return {
      model: '',
      error: '',
    }
  },
})
</script>

<template>
  <div>
    <input
        v-model="model"
        :name="name"
        type="tel"
        :id="'telephone'"
        :disabled="disabled"
        class="form-control font-main"
        autocomplete="off"
        :placeholder="placeholder"
        :class="{ 'is-invalid': hasError}"
        :required="required"
        ref="maskPhone"
    />
    <span role="alert" class="text-red" v-if="hasError">
      {{ error }}
    </span>
  </div>
</template>

<style scoped lang="sass">
.is-invalid
  border: 1px solid red
input
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
