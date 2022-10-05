<template>
  <main class="main">
    <formVue />
  </main>
</template>

<script>
import formVue from "../form.vue";
export default {
  name: "mainVue",
  components: {
    formVue,
  },
};
</script>

<style lang="scss" scoped>
.main {
  height: 100%;
  padding: 20px;
}
</style>