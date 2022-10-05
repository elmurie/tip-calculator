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
  background: rgba(255, 255, 255, 0.103);
  background-image: url('../../assets/img/money-bg.jpg');
  background-blend-mode: multiply;
  display: flex;
  align-items: center;
  height: 100%;
  padding: 20px;
}
</style>