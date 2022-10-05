<template>
  <header class="header">
    <div class="icon">
      <font-awesome-icon
        icon="fa-solid fa-hand-holding-dollar"
        size="3x"
        shake
        inverse
        style="--fa-animation-delay: 3s; --fa-animation-iteration-count: 3"
      />
    </div>
    <h1 class="title">Tip Calculator</h1>
  </header>
</template>

<script>
export default {
  name: "headerVue",
};
</script>

<style lang="scss" scoped>
@import '../../assets/style/variables.scss';
@import '../../assets/style/common.scss';
.header {
  font-family: $headingFontFamily;
  padding: 20px;
  background: linear-gradient(to top, $second 0%, transparent 70%),
    linear-gradient(to bottom, transparent, rgba($white, 0.4) 70%), $third;
  animation: bg 10s infinite;

  @keyframes bg {
    0%,
    100% {
      background-color: $first;
    }
    20% {
      background-color: $second;
    }
    40% {
      background-color: $third;
    }
    60% {
      background-color: $fourth;
    }
    80% {
      background-color: $fifth;
    }
  }

  .title {
    color: $white;
    text-transform: uppercase;
  }
  .icon {
    margin-bottom: 20px;
  }
}

@media screen and (max-width: 768px) {
  .header {
    padding: 10px;
  }
}
</style>