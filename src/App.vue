<template>
  <div id="app">
    <Form @submitForm='onSubmitNewItem'/>
    <TotalBalance :total='totalBalance'/>
    <Budgetlist :list='list' @deleteItem="onDeleteItem"/>
  </div>
</template>

<script>
import Budgetlist from '@/components/BudgetList.vue';
import TotalBalance from '@/components/TotalBalance.vue';
import Form from '@/components/Form.vue';

export default {
  name: 'App',
  components: {
    Budgetlist,
    TotalBalance,
    Form,
  },
  data: () => ({
    list: {
      0: {
        id: 0,
        type: 'Приход',
        value: 50,
        comment: 'Аванс',
      },
      1: {
        id: 1,
        type: 'Расход',
        value: -30,
        comment: 'Купила сапог',
      },
      2: {
        id: 2,
        type: 'Приход',
        value: 50,
        comment: 'Зарплата',
      },
    },
  }),
  computed: {
    totalBalance () {
      return Object.values(this.list).reduce((acc, item)=>acc + item.value, 0);
    },
  },
  methods: {
    onDeleteItem(id) {
      this.$delete(this.list, id);
    },
    onSubmitNewItem(data) {
      const newObj = {
        ...data,
        id: String(Math.random())
      };
      this.$set(this.list, newObj.id, newObj);
    },
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}
</style>
