<template>
  <div class="login_container">
    <div class="login_box">
      <div class="avatar_box">
        <img src="../assets/logo.png" alt="">
      </div>
      <el-form ref="loginFormRef" :model="loginInfo" :rules="rules" class="login_form" label-width="80px">
        <el-form-item label=用户名 prop="username">
          <el-input v-model="loginInfo.username" placeholder="请输入用户名" prefix-icon="el-icon-user" :clearable=true></el-input>
        </el-form-item>
        <el-form-item label=密码 prop="password">
          <el-input v-model="loginInfo.password" placeholder="请输入密码" prefix-icon="el-icon-lock" type="password" :clearable=true></el-input>
        </el-form-item>
        <el-form-item label="">
          <el-button class="login_button" type="primary" v-on:click="login" >登陆</el-button>
          <el-button class="login_button" type="info" v-on:click="resetLoginForm" >清除</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      loginInfo: {
        username: '',
        password: ''
      },
      // 表单的验证规则
      rules: {
        // 验证用户名
        username: [
          { required: true, message: '请输入用户名', trigger: 'blur' },
          { min: 3, max: 10, message: '输入长度在3到5个字符', trigger: 'blur' }
        ],
        // 验证密码
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' },
          { min: 3, max: 10, message: '输入长度在3到5个字符', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    resetLoginForm () {
      this.$refs.loginFormRef.resetFields()
    },
    login () {
      this.$refs.loginFormRef.validate(valid => {
        if (!valid) return
        this.$message.success('登陆成功')
        window.sessionStorage.setItem('token', '11112222222222')
        // router跳转到主界面
        this.$router.push('/home')
      })
    }
  }
}
</script>

<style lang="less" scoped>
.login_container{
  background-color: #2b4b6b;
  height: 100%;
}
.login_box{
  width: 450px;
  height: 300px;
  background-color: #fff;
  border-radius: 5px;
  position:absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
.avatar_box{
  height: 130px;
  width: 130px;
  border: 1px solid #eee;
  border-radius: 50%;
  padding: 10px;
  box-shadow: 0 0 10px #eee;
  position:absolute;
  left: 50%;
  top: 0%;
  transform: translate(-50%, -50%);
  background-color: #fff;
  img {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background-color: #eee;
  }
}
.login_form{
  position: absolute;
  bottom: 0;
  width: 100%;
  padding: 0 10px;
  box-sizing: border-box;
}
.btns{
  display: flex;
  justify-content: flex-end;
}
</style>
