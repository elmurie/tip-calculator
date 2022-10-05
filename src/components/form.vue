<template>
  <form class="form" @submit.prevent>
    <div class="form__price">
      <label for="price">How much is the bill?</label>
      <input
        name="price"
        type="number"
        step=".01"
        v-model="price"
      />
    </div>
    <div class="form__percentage">
      <label for="percentage">Tip</label>
      <input type="range" name="percentage" step="5" v-model="percentage"/>
      <div class="display">{{ percentage }}%</div>
    </div>
    <div class="form__tip">
      <div class="tip__amount">Tip amount {{ calcTip }}</div>
      <div class="bill__total">Total with tip {{ calcTotal }}</div>
    </div>
  </form>
</template>


<script>
export default {
  name: "formVue",
  data() {
    return {
      price: 0,
      percentage: 0,
    };
  },
  methods: {
    // restrictDecimal() {
    //   this.price = this.price.match(/^\d+\.?\d{0,2}/);
    // },
  },
  computed: {
    calcTip: function () {
      if (this.price !== "" && this.price !== null) {
        return parseFloat((parseFloat(this.price) / 100) * parseInt(this.percentage)).toFixed(2);
      } else {
        return 0;
      }
    },
    calcTotal: function () {
        return parseFloat(parseFloat(this.price) + parseFloat(this.calcTip)).toFixed(2);
      
    },
  },
};
</script>

<style lang="scss" scoped>
.form {
  font-size: 50px;
  &__price {
    display: flex;
    flex-direction: column;
    input {
      max-width: 500px;
      margin: 5px auto;
    }
  }
  &__percentage {
    input {
      width: 70%;
    }
  }
}
</style>