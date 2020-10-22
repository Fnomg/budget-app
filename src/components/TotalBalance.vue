<template>
  <div class="total-balance__wrap">
<!--     <el-card class="total-balance__card">
      <div>Осталось в кошельке : {{total}} </div>
    </el-card> -->
    <span>Осталось в кошельке : {{total}}</span>
  </div>
</template>

<script>
export default {
  name: 'TotalBalance',
  props: {
    total: {
      type: Number,
      default: 0,
    },
  },
}
</script>

<style scoped>
.total-balance__wrap {
  margin: 30px 0;
  text-transform: uppercase;
}
</style>