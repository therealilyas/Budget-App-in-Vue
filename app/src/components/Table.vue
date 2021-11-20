<template>
  <div id="app">
    <div class="income-table">
      <h3>Income</h3>
      <div class="income-list" v-for="(item, index) of incomes" :key="index">
        <p>
          {{ item.notes }} <br />
          ${{ item.money }}
        </p>
      </div>
    </div>
    <div class="expence-table">
      <h3>Expence</h3>
      <div class="expence-list" v-for="(item, index) of expences" :key="index">
        <p>
          {{ item.notes }} <br />
          ${{ item.money }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Table",
  props: ["incomes", "expences"],
  data() {
    return {};
  },
  methods: {},
};
</script>

<style lang='scss' scoped>
@mixin tables($color) {
  display: flex;
  flex-direction: column;
  padding: 1rem;
  width: 50%;
  color: $color;
  border-right: 1px solid black;
}
@mixin item($color) {
  cursor: pointer;
  margin: 1rem;
  text-align: center;
  width: 15%;
  padding: 5px 0 5px 0;
  border: 2px solid $color;
  border-radius: 5px;
}

#app {
  display: flex;
  justify-content: space-between;
  width: 100%;
  height: 30rem;
  .income-table {
    @include tables(green);
    h3 {
      margin-left: 15rem;
    }
    .income-list {
      p {
        @include item(green);
      }
    }
  }
  .expence-table {
    @include tables(red);
    h3 {
      margin-left: 15rem;
    }
    .expence-list {
      p {
        @include item(red);
      }
    }
  }
}
</style>