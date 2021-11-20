<template>
  <div id="app">
    <div class="input-form">
      <h1>Input</h1>
      <input
        v-model="notes"
        type="text"
        name="notes"
        placeholder="Notes"
        class="notes"
      />
      <input
        v-model="money"
        type="number"
        name="money-value"
        placeholder="Money"
        class="money-value"
      />
      <div class="buttons">
        <button class="add-income-btn" @click="addIncome">Add Income</button>
        <button class="add-expence-btn" @click="addExpences">
          Add Expence
        </button>
      </div>
    </div>

    <div class="balance-container">
      <h2>Balance: $ {{ this.myBalance }}</h2>
      <div class="balance-form">
        <input
          v-model="balance"
          type="number"
          name="balance"
          placeholder="Balance"
          class="balance"
        />
        <button class="add-balance-btn" @click="addBalance">Add Balance</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "inputForm",
  props: ["myBalance"],
  data() {
    return {
      money: "",
      notes: "",
      balance: "",
    };
  },
  methods: {
    addIncome() {
      if (this.money !== "" && this.notes !== "") {
        this.$emit("addIncome", this.money, this.notes);
        this.money = "";
        this.notes = "";
      }
    },
    addExpences() {
      if (this.money !== "" && this.notes !== "") {
        this.$emit("addExpences", this.money, this.notes);
        this.money = "";
        this.notes = "";
      }
    },
    addBalance() {
      console.log("Balance Btn Pressed");
      this.$emit("addBalance", this.balance);
      this.balance = "";
    },
  },
};
</script>

<style lang='scss' scoped>
@mixin add-btn($bg-color, $color) {
  outline: none;
  color: $color;
  background-color: $bg-color;
  padding: 5px;
  border: 2px solid $bg-color;
  border-radius: 5px;
  opacity: 1;
  transition: 0.3s ease-in;
  &:hover {
    background-color: $color;
    color: $bg-color;
  }
}

#app {
  margin-top: 1rem;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;

  .input-form {
    margin-left: 5rem;
    display: flex;
    flex-direction: column;
    padding-bottom: 0.5rem;
    input {
      margin-top: 1rem;
      padding: 5px;
      border: 1px solid gray;
      border-radius: 5px;
    }
    .buttons {
      margin-top: 1rem;
      .add-income-btn {
        @include add-btn(green, white);
        margin-right: 1rem;
      }
      .add-expence-btn {
        @include add-btn(red, white);
      }
    }
  }
  .balance-container {
    margin-right: 5rem;
    display: flex;
    flex-direction: row;
    .balance-form {
      width: 100px;
      margin-left: 2rem;
      display: flex;
      flex-direction: column;
      input {
        padding: 5px;
        border: 1px solid gray;
        border-radius: 5px;
      }
      .add-balance-btn {
        margin-top: 1rem;
        @include add-btn(blue, white);
      }
    }
  }
}
@media (max-width: 1000px) {
  #app {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
}
</style>