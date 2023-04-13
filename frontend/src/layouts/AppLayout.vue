<template>
  <div>
    <app-header />
    <slot />
  </div>
</template>

<script>
import AppHeader from "./AppHeader.vue";
export default {
  name: "AppLayout",
  components: {AppHeader}
}
</script>

<style scoped>

</style>
