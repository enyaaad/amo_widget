<script setup lang="ts">
  import ActivationWindow from "@/components/UI/ActivationWindow.vue";
</script>

<template>
  <main class="main-content">
    <section class="main-window">
      <activation-window/>
    </section>
  </main>
</template>

<style scoped lang="sass">
.main-content
  display: flex
  justify-content: center
  .main-window
    width: 60%
</style>
