<template>
   <div class="login_container">
      <div class="header">
        <mt-header title="登录">
            <mt-button icon="back" @click="back" slot="left">返回</mt-button>
        </mt-header>
      </div>
     <div class="content">
       <div class="box">
         <div class="icon user_icon"></div>
         <input v-model="userName" type="text" placeholder="请输入用户名/手机号" v-focus ref="inputfocus">
       </div>
       <div class="box">
         <div class="icon password_icon"></div>
         <input v-model="password" type="password" placeholder="请输入密码（6--12个字符）">
       </div>
       <button @click="login" class="login">登录</button>
       <div class="bottom">
         <div class="sign_up">立即注册</div>
         <div class="forget_password">忘记密码？</div>
       </div>
     </div>
    <!-- <div class="header">
        <mt-header title="登录">
            <mt-button icon="back" @click="back" slot="left"></mt-button>
        </mt-header>
     </div>
    <div class="login_box">
         <mt-field label="用户名" placeholder="请输入用户名" v-model="userName"></mt-field>
         <mt-field label="密码" placeholder="请输入密码" type="password" v-model="password"></mt-field>
         <mt-button type="primary" @click="login">登录</mt-button>
    </div> -->
   </div>
</template>
<script>
import {Toast} from 'mint-ui'
import { XInput } from 'vux'
export default {
  data () {
    return {
      userName: '',
      password: ''
    }
  },
  mounted () {
    this.$refs.inputfocus.focus()
  },
  methods: {
    back () {
      this.$router.go(-1)
    },
    login () {
      if (this.userName.trim() === '') {
        Toast({
          message: '请填写用户名',
          position: 'middle',
          duration: 1000
        })
        return false
      }
      if (this.password.trim() === '') {
        Toast({
          message: '请填写密码',
          position: 'middle',
          duration: 1000
        })
        return false
      }
      //   const {userName, password} = this
      this.$store.dispatch('login', this)
    }
  },
  components: {
    XInput
  },
  directives: {
    focus: {
      inserted: function (el) {
        el.focus()
      }
    }
  }
}
</script>
<style scoped>
.login_container{
  width: 100%;
  font-family: PingFangSC-Regular;
  display:flex;
  flex-direction: column;
}
.content{
  width: 78%;
  margin: 0 auto;
  flex: 0 0 58%;
}
.header{
  margin-bottom: 10%;
  width: 100%;
  height: 245px;
  background-size:100% 100%;
  background-repeat: no-repeat;
  background-image: url('img/banner@2x.png');
  flex:1;
}
.mint-header{
  background:rgba(0,0,0,0);
  font-size: 17px;
}
.mint-header-title{
  font-size: 20px;
}
.box{
  opacity: 0.7;
  background: #FFFFFF;
  box-shadow: inset 0 0 1px 0 rgba(0,0,0,0.50);
  border-radius: 5px;
  width: 96%;
  margin: 0 auto;
  height: 44px;
  display: flex;
  align-items:center;
  padding-right: 4%;
  margin-top: 25px;
}
.box .icon{
  flex: 0 0 12%;
  width: 18px;
  height: 20px;
  margin-left:3.2%;
  background-size:18px 20px;
  background-repeat: no-repeat;
}
.user_icon{
  background-image: url('img/user@2x.png');
}
.password_icon{
  background-image: url('img/password@2x.png');
}
.box input{
  flex:1;
  height: 22px;
  font-size: 15px;
  color: #797979;
  letter-spacing: 0.15px;
  border: none;
}
.login{
  margin-top: 45px;
  width: 100%;
  height: 45px;
  line-height: 45px;
  opacity: 0.7;
  background: #0088EB;
  border: none;
  box-shadow: 0 2px 3px 0 rgba(112,112,112,0.50);
  border-radius: 5px;
  font-size: 18px;
  color: #FFFFFF;
  letter-spacing: 0.14px;
}
.bottom{
  margin-top: 23px;
  display: flex;
  justify-content: space-between;
}
.bottom div{
  font-size: 15px;
  color: #8E8E93;
  letter-spacing: 0.15px;
}
.forget_password{
  text-decoration:underline;
}
@media (-webkit-min-device-pixel-ratio: 3), (min-device-pixel-ratio: 3) {
  .user_icon{
    background-image: url('img/user@3x.png');
  }
  .password_icon{
    background-image: url('img/password@3x.png');
  }
  .header{
    background-image: url('img/banner@3x.png');
  }
}

</style>
