<template>
  <div class="header">
    <el-row class="main" type='flex'>
      <div class="logo">
        <nuxt-link to='/'>
          <img src="http://157.122.54.189:9093/images/logo.jpg" alt="">
        </nuxt-link>
      </div>
      <el-row type='flex' class="nav">
        <nuxt-link to='/'>首页</nuxt-link>
        <nuxt-link to='/post'>旅游攻略</nuxt-link>
        <nuxt-link to='/hotel'>酒店预订</nuxt-link>
        <nuxt-link to='/air'>国内机票</nuxt-link>
      </el-row>
      <div class="header-right">
        <div v-if="$store.state.user.userInfo.token">
          <el-dropdown>
            <span class="el-dropdown-link">
              <img 
              :src="$axios.defaults.baseURL + $store.state.user.userInfo.user.defaultAvatar" 
              alt=""
              >
              {{$store.state.user.userInfo.user.nickname}}
              <i class="el-icon-arrow-down el-icon--right"></i>
            </span>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item>个人中心</el-dropdown-item>
              <el-dropdown-item>
                <div @click='handleClick'>退出登录</div>
              </el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
        </div>
        <div class="login" v-else @click="handleLogin">
          登录/注册
        </div>
      </div>
    </el-row>
  </div>
</template>
<script>
export default {
  methods: {
    handleClick(){
      // alert(123)
      this.$store.commit('user/clearUserInfo'),
      this.$message.success("退出成功"),
      this.$router.push("/user/login")
    },
    handleLogin(){
      this.$router.push("/user/login")
    }
  },
}
</script>
<style lang="less">
  .header{
    height: 60px;
    line-height: 60px;
    border-bottom:1px #ddd solid;
    .main{
      width: 1000px;
      margin:0 auto;

      .logo{
        margin-top:9px;
        margin-right:20px;

        img{
          display:block;
          width: 156px;
          height: 42px;
        } 
      }
      .nav{
          flex:1;
            a{
              display:block;
              padding: 0 20px;
              height: 60px;
              box-sizing: border-box;

              &:hover{
                color:#409eff;
                border-bottom:5px #409eff solid;
              }
              &:active{
                background:#409eff;
                color:#fff;
              }
            }
            .nuxt-link-exact-active{
                background:#409eff;
                color:#fff!important;
            }
        }
      //登录注册页的样式
      .el-dropdown-link{
        img{
          width: 40px;
          height: 40px;
          border-radius: 40px;
          vertical-align: middle;
        }
      }
    }
  }
</style>
