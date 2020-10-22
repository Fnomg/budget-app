<template>
  <div class="form__wrap">
    <el-card>
      <el-form :model="formData" ref="addItemForm" :rules="rules" label-position='right'>
         <el-form-item label="Тип операции" prop="type">
          <el-select v-model="formData.type" placeholder="Выбери тип, детка...">
            <el-option label="Приход" value="Income" />
            <el-option label="Расход" value="Outcome" />
          </el-select>
        </el-form-item>
        <el-form-item label="Где деньги, Лебовски?" prop="comment">
          <el-input type="text" v-model="formData.comment" />
        </el-form-item>
        <el-form-item label="Сумма" prop="value">
          <el-input v-model.number="formData.value" />
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit" round>Создать</el-button>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script>
export default {
  name: 'Form',
  data: () => ({
    formData: {
      type: 'Income',
      comment: '',
      value: 0,
    },
    rules: {
      comment: [
      { required: true, message: 'Расскажи мне все', trigger: 'blur' },
      { min: 3, max: 100, message: 'От 3 до 100 символов.', trigger: 'blur' }
      ],
      value: [
      { required: true, message: 'Сколько, сколько?', trigger: 'blur' },
      { type: 'number', message: 'Меня интересуют только цифры', trigger: 'change' }
      ],
    },
  }),
  methods: {
    onSubmit() {
      this.$refs.addItemForm.validate(valid => {
        if (valid) {
          this.$emit('submitForm', { ...this.formData });
          this.$refs.addItemForm.resetFields();
        }
      });
    },
  },
}

</script>

<style scoped>
.form__wrap{
  max-width: 450px;
  margin: auto;
  margin-bottom: 5px;
}
</style>