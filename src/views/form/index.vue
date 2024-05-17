

<template>
  <div class="app-container">
    <el-form ref="form" :model="form" label-width="auth">
      <el-form-item label="数电账号">
        <el-input v-model="form.name" />
      </el-form-item>
      <el-form-item label="省份是否开启智能扫码">
        <el-switch v-model="form.delivery" />
      </el-form-item>
      <el-form-item label="实人认证照片">
        <el-upload  :file-list="fileList" action="" multiple :auto-upload="false" :on-change="getFile" list-type="picture-card">
          <i class="el-icon-plus"></i>
        </el-upload>
      </el-form-item>

      <el-form-item>
        <el-button type="primary" @click="onSubmit">提交添加/更新</el-button>
        <el-button @click="onCancel">取消</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      form: {
        name: '',
        delivery: false,
        imagedate:[]
      },
      fileList:[]
    }
  },
  methods: {
    getBase64(file){
    return new Promise(function(resolve,reject){
      let reader = new FileReader();
      let imgResult = "";
      reader.readAsDataURL(file);
      reader.onload = function(){
        imgResult = reader.result;
      };
      reader.onerror = function(error){
        reject(error);
      };
      reader.onloadend = function(){
        resolve(imgResult);
      };
      });
    },
    getFile(file,fileList){
      this.getBase64(file.raw).then(res => {
      console.log(res)
      });
    },

    onSubmit() {
    let a = this.form
    a.imagedate =
    console.log(a)
    axios.post('https://127.0.0.1/adddigitaccount', this.form)
      this.$message({
        message: '提交成功!',
        type: 'success'
      })
    },
    onCancel() {
      this.$message({
        message: '取消!',
        type: 'warning'
      })
    }
  }
}
</script>

<style scoped>
.line{
  text-align: center;
}
</style>
