<template>
  <form class="form" @submit.prevent>
    <div class="form__price">
      <label for="price">How much is the bill?</label>
      <input
        name="price"
        type="number"
        step=".01"
        v-model="price"
        @input="restrictDecimal"
      />
    </div>
    <div class="form__percentage">
      <label for="percentage">Tip</label>
      <input type="range" name="percentage" step="5" v-model="percentage" />
      <div class="display">{{ percentage }}%</div>
    </div>
    <div class="form__total">
      <div class="tip__amount">Tip amount</div>
      <strong>{{ calcTip }}</strong>
      <div class="bill__total">Total with tip</div>
      <strong>{{ calcTotal }}</strong>
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
    restrictDecimal() {
      this.price = this.price.match(/^\d+\.?\d{0,2}/);
    },
  },
  computed: {
    calcTip: function () {
      if (this.price !== "" && this.price !== null) {
        return parseFloat(
          (parseFloat(this.price) / 100) * parseInt(this.percentage)
        ).toFixed(2);
      } else {
        return 0;
      }
    },
    calcTotal: function () {
      if (this.price !== "" && this.price !== null) {
        return parseFloat(
          parseFloat(this.price) + parseFloat(this.calcTip)
        ).toFixed(2);
      } else {
        return 0;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.form {
  width: 100%;
  height: fit-content;
  &__price {
    display: flex;
    flex-direction: column;
    label {
      font-size: 40px;
    }
    input {
      background-color: #f3f3f3;
      border: 2px solid #e3e8e6;
      border-radius: 25px;
      padding: 10px;
      outline: none;
      height: 48px;
      font-size: 50px;
      text-align: center;
      max-width: 250px;
      margin: 10px auto;
    }
  }
  &__percentage {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 20px;
    label, .display {
      font-size: 20px;
    }
    input[type="range"] {
      background: transparent;
      height: 32px;
      appearance: none;
      -webkit-appearance: none;
      margin: 10px 0;
      width: 70%;
    }
    input[type="range"]:focus {
      outline: none;
    }
    input[type="range"]::-webkit-slider-runnable-track {
      width: 100%;
      height: 6px;
      cursor: pointer;
      box-shadow: 1px 1px 2px #9e9e9e;
      background: #e3e8e6;
      border-radius: 10px;
      border: 0px solid #ffffff;
    }
    input[type="range"]::-webkit-slider-thumb {
      box-shadow: 0px 0px 0px #000000;
      border: 1px solid #ffffff;
      height: 25px;
      width: 16px;
      border-radius: 10px;
      background: #4b47a9;
      cursor: pointer;
      appearance: none;
      -webkit-appearance: none;
      margin-top: -10px;
    }
    input[type="range"]:focus::-webkit-slider-runnable-track {
      background: #e3e8e6;
    }
    input[type="range"]::-moz-range-track {
      width: 100%;
      height: 6px;
      cursor: pointer;
      box-shadow: 1px 1px 2px #9e9e9e;
      background: #e3e8e6;
      border-radius: 10px;
      border: 0px solid #ffffff;
    }
    input[type="range"]::-moz-range-thumb {
      box-shadow: 0px 0px 0px #000000;
      border: 1px solid #ffffff;
      height: 25px;
      width: 16px;
      border-radius: 10px;
      background: #4b47a9;
      cursor: pointer;
    }
    input[type="range"]::-ms-track {
      width: 100%;
      height: 6px;
      cursor: pointer;
      background: transparent;
      border-color: transparent;
      color: transparent;
    }
    input[type="range"]::-ms-fill-lower {
      background: #e3e8e6;
      border: 0px solid #ffffff;
      border-radius: 20px;
      box-shadow: 1px 1px 2px #9e9e9e;
    }
    input[type="range"]::-ms-fill-upper {
      background: #e3e8e6;
      border: 0px solid #ffffff;
      border-radius: 20px;
      box-shadow: 1px 1px 2px #9e9e9e;
    }
    input[type="range"]::-ms-thumb {
      margin-top: 1px;
      box-shadow: 0px 0px 0px #000000;
      border: 1px solid #ffffff;
      height: 25px;
      width: 16px;
      border-radius: 10px;
      background: #4b47a9;
      cursor: pointer;
    }
    input[type="range"]:focus::-ms-fill-lower {
      background: #e3e8e6;
    }
    input[type="range"]:focus::-ms-fill-upper {
      background: #e3e8e6;
    }
  }
  &__total {
    max-width: 70%;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    margin: 50px auto;
    font-size: 35px;
    row-gap: 20px;
    align-items: center;
  }
}
@media screen and (max-width: 768px) {
  .form {
    padding: 0;
    &__price {
      label {
        font-size: 30px;
      }
    }
    &__total {
      max-width: 100%;
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      margin: 50px auto;
      font-size: 20px;
    }
  }
}
</style>