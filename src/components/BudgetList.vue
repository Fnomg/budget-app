<template>
  <div class="budget-list__wrap">
    <el-card :header="header" class="budget-list__card">
      <template v-if="isEmpty">
        <div v-for="(item, prop) of list" :key="prop" class="budget-list__item">
          <span class="item__comment">{{item.comment}}</span>
          <span class="item__value">{{item.value}}</span>
          <el-button @click='deleteItem(item.id)' type="danger" icon="el-icon-delete" circle size="mini"></el-button>
      </div>
      </template>
      <el-alert v-else :title="alertTitle" type="info" show-icon :closable='false'/>
    </el-card>
  </div>
</template>

<script>
export default {
  name: 'Budgetlist',
  data: () => ({
    header: 'Легко пришли / легко ушли',
    alertTitle: 'Внеси данные, детка',
  }),
  props: {
    list: {
      type: Object,
      default: () => ({}),
    },
  },
  methods: {
    deleteItem(id) {
      this.$emit('deleteItem', id);
    },
  },
  computed: {
    isEmpty() {
      return Object.keys(this.list).length;
    }
  }
};
</script>

<style scoped>
.budget-list__wrap{
  max-width: 450px;
  margin: auto;
}
.budget-list__item{
  display: flex;
  margin-bottom: 5px;
  align-items: center;
}
.item__value {
  margin-right: 20px;
  margin-left: auto;
}
</style>