<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  name: "UserNote",
})
</script>

<template>
  <div class="usernote-content">
    <span class="content-text">
      <slot/>
    </span>
  </div>
</template>

<style scoped lang="sass">
.usernote-content
  display: flex
  width: 100%
  height: 100%
  .content-text
    padding: 8px 12px
    box-sizing: border-box
    float: right
    line-height: 14px
    background-color: #E8EEEF
    border-radius: 4px


</style>
