<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  name: "WindowHeader"
})
</script>

<template>
  <div class="header-content">
    <span class="font-header">
      <slot/>
    </span>
  </div>
</template>

<style scoped lang="sass">
.header-content
  background-color: #BACBCE
  color: #303133
  padding: 16px 80px
  width: 100%
  display: flex
  flex-direction: row
  justify-content: center
  .font-header
    text-align: center
@media(min-width: 768px)
  .header-content
    white-space: nowrap

</style>
