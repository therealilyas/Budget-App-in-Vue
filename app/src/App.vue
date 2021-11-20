<template>
  <div id="app">
    <InputForm
      @addIncome="addIncome"
      @addExpences="addExpences"
      :myBalance="myBalance"
      @addBalance="addBalance"
    />
    <Table :incomes="incomes" :expences="expences" />
  </div>
</template>

<script>
import InputForm from "./components/InputForm.vue";
import Table from "./components/Table.vue";

export default {
  components: {
    InputForm,
    Table,
  },
  data() {
    return {
      incomes: [],
      expences: [],
      myBalance: 0,
    };
  },
  methods: {
    addIncome(money, notes) {
      let item = {
        money: money,
        notes: notes,
      };
      this.myBalance = this.myBalance + money;
      this.incomes.push(item);
      console.log(this.incomes);
    },
    addExpences(money, notes) {
      let item = {
        money: money,
        notes: notes,
      };
      this.myBalance = this.myBalance - money;
      this.expences.push(item);
      console.log(this.expences);
    },
    addBalance(balance) {
      this.myBalance = this.myBalance + balance;
    },
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Cousine&display=swap");
* {
  font-family: "Cousine", monospace;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
html {
  width: 100%;
  height: 100%;
}
body {
  width: 100%;
  height: 100%;
}
button {
  cursor: pointer;
  outline: none;
}
</style>
