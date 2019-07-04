<template>
  <div class='loginform'>
    <el-form
    :model="form"
    :rules="rules"
    ref="form"
    >
      <el-form-item prop='username'>
        <el-input 
        placeholder="请输入用户名" 
        v-model="form.username">
        </el-input>
      </el-form-item>

      <el-form-item prop='password'>
        <el-input 
        placeholder="请输入密码" 
        v-model="form.password">
        </el-input>
      </el-form-item>
      <el-button 
      class='login' 
      type='primary' 
      @click="handleLoginSubmit">
      登录
      </el-button>
    </el-form>
  </div>
</template>

<script>
export default {
  data(){
    return {
      form:{
        username:"",
        password:""
      },
      rules:{
        username:[
          {required:true, message:'请输入用户名',trigger:'blur'}
        ],
        password:[
          {required:true, message:'请输入密码',trigger:'blur'}
        ]
      }  
    }
  },
  methods: {
        handleLoginSubmit(){
          this.$refs.form.validate(valid=>{
            if(valid){
              this.$axios({
                url:"/accounts/login",
                method:'POST',
                data:this.form
              }).then(res=>{
                // console.log(res.data)
                this.$store.commit("user/setUserInfo", res.data),
                this.$router.push('/')
              })
            }
          })
        }
      }
}
</script>

<style lang="less">
  .loginform{
    padding:25px;
  }
  .login{
    width: 100%;
  }
</style>
