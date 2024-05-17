import axios from 'axios'


<template>
  <div class="app-container">
    <el-form ref="form" :model="form" label-width="120px">
      <el-form-item label="数电账号" >
        <el-input v-model="form.name" />
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit1">提交登录</el-button>
        <el-button type="primary" @click="onSubmit2">提交认证</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        name: '',
        delivery: false,
        imagedate:''
      }
    }
  },
  methods: {
    onSubmit1() {
    axios.post('https://127.0.0.1/logindigitaccount', this.data.form)
      this.$message({
        message: '提交成功!',
        type: 'success'
      })
    },
    onSubmit2() {
    axios.post('https://127.0.0.1/verfitydigitaccount', this.data.form)
      this.$message({
        message: '提交成功!',
        type: 'success'
      })
    },
  }
}
</script>

<style scoped>
.line{
  text-align: center;
}
</style>
