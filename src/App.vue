<template>
  <div id="app">
    <headerVue/>
    <mainVue/>
    <footerVue/>
  </div>
</template>

<script>
import headerVue from './components/layout/header.vue';
import mainVue from './components/layout/main.vue';
import footerVue from './components/layout/footer.vue';
export default {
  name: 'App',
  components: {
    headerVue,
    mainVue,
    footerVue,
  }
}
</script>

<style lang="scss">
@import './assets/style/common';
#app {
  height: 100vh;
  display: flex;
  flex-direction: column;
}
</style>
