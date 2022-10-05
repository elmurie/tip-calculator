<template>
  <footer class="footer">
    <div class="footer__desc">{{ description }}</div>
    <div class="footer__social">
      <a class="footer__social__link" :href="links.portfolio">
        <font-awesome-icon icon="fa-solid fa-user" size="2x" inverse />
      </a>
      <a class="footer__social__link" :href="links.linkedin">
        <font-awesome-icon icon="fa-brands fa-linkedin" size="2x" inverse />
      </a>
      <a class="footer__social__link" :href="links.github">
        <font-awesome-icon icon="fa-brands fa-github" size="2x" inverse />
      </a>
      <a class="footer__social__link" :href="links.email">
        <font-awesome-icon icon="fa-solid fa-at" size="2x" inverse />
      </a>
    </div>
  </footer>
</template>

<script>
export default {
  name: "footerVue",
  data() {
    return {
      description: "Developed by Simone Morieri",
      links: {
        portfolio: "https://morieri.netlify.app/",
        linkedin: "https://www.linkedin.com/in/simone-morieri/",
        github: "https://github.com/elmurie",
        email: "mailto:elmurie@gmail.com",
      },
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/style/variables.scss";
.footer {
  color: $white;
  background-color: $third;
  margin-top: auto;
  padding: 30px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  &__social {
    display: flex;
    gap: 10px;
    &__link {
      transition: all 0.5s;
      &:hover {
        transition: all 0.5s;
        transform: translateY(-5px);
      }
    }
  }
}
@media screen and (max-width: 768px) {
  .footer {
    flex-direction: column;
    padding: 10px;
    gap: 5px;
  }
}
</style>