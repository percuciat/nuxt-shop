<template>
  <div class="container mx-auto">
    <base-header/>
    <Nuxt/>
  </div>
</template>

<script>
  export default {
    name: "blog-template",
  }
</script>

<style scoped>
  .page-enter-active,
  .page-leave-active {
    transition: opacity 0.5s;
  }
  .page-enter,
  .page-leave-to {
    opacity: 0;
  }
</style>
