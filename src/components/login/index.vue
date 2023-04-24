<template>
  <div class="login">
    <div class="login_box">
      <div class="avatar">
        <img src="@/assets/logo.png">
      </div>
      <el-form ref="form" class="form" :model="userInfo" :rules="loginRules">
        <el-form-item prop="username">
          <el-input placeholder="请输入用户名"
            prefix-icon="el-icon-user"
            v-model="userInfo.username">
          </el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input placeholder="请输入密码"
          type="password"
            prefix-icon="el-icon-lock"
            v-model="userInfo.password">
          </el-input>
        </el-form-item>
        <el-form-item class="item">
           <el-button type="primary" size="mini" @click="login">登录</el-button>
           <el-button type="info" size="mini" @click="reset">重置</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data(){
 return{
   userInfo:{
    username:'',
    password:''
   },
   loginRules:{
   username:[
     { required: true, message: '请输入用户名', trigger: 'blur' },
     { min: 3, max: 10, message: '长度在 3 到 10 个字符', trigger: 'blur' }
   ],
   password:[
      { required: true, message: '请输入密码', trigger: 'blur' },
     { min: 3, max: 10, message: '密码长度在 3 到 10 个字符', trigger: 'blur' }
   ]
   }
 }
  },
  methods:{
    // 重置表单
    reset(){
        this.$refs.form.resetFields();
    },
    login(){
      this.$refs.form.validate((valid)=>{
        // valid为布尔值
        if(!valid) return 
      })
    }
  }

}
</script>

<style lang="less" scoped>
 .login{
  width: 100%;
  height: 100%;
  background-color:#204969;
  .login_box{
    width: 400px;
    height: 300px;
    background-color: #fff;
    position:absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
    .avatar{
      width: 130px;
      height: 130px;
      border-radius: 50%;
      background-color: #fff;

      position: absolute;
      left: 50%;
      transform: translate(-50%,-50%);
      img{
        width: 100%;
        height: 100%;
        border-radius: 50%;
        background-color: grey;
        box-shadow: 5px 5px 5px #f2f4f6;
      }
    }
    .form{
      position: absolute;
      bottom: 0;
      width: 100%;
      padding: 0 20px;
      box-sizing: border-box;
      .item{
      display: flex;
      justify-content: flex-end;
    }
    }

  }

 }


</style>