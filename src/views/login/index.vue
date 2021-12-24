/* eslint-disable no-tabs */
<template>
  <div class="login-container">
      <van-nav-bar
  title="登录"
  />
  <van-form @submit="onSubmit">
    <van-field
      name="手机号"
      placeholder="请输入手机号"
      v-model="user.mobile"
    >
    <i slot="left-icon" class="iconfont shouji">&#xe615;</i>
    </van-field>
    <van-field
      name="验证码"
      placeholder="请输入验证码"
      v-model="user.code"
    >
    <i slot="left-icon" class="iconfont shouji">&#xe610;</i>
     <template #button>
        <van-button round size="small" type="default" class="send-sms-btn">发送验证码</van-button>
      </template>
    </van-field>
    <div class="login-btn-wrap">
      <van-button  class="login-btn" block type="info" native-type="submit">登录</van-button>
    </div>
  </van-form>
  </div>
</template>

<script>
import { login } from '@/api/user.js'
export default {
  name: 'loginindex',
  data () {
    return {
      user: {
        mobile: '', // 手机号
        code: '' // 验证码
      }
    }
  },
  methods: {
    async onSubmit () {
      const user = this.user
      try {
        const res = await login(user)
        console.log('登录成功', res)
      } catch (err) {
        console.log('登录失败', err)
      }
    }
  }
}
</script>

<style>
body {
  background-color: #f5f7f9;
}
.iconfont {
  font-size: 37px;
}
.send-sms-btn {
  width: 164px;
  height: 46px;
  background-color: #ededed;
  border-radius: 23px;
  font-size: 22px;
}
.login-btn-wrap {
  margin-top: 53px;
  margin-left: 28px;
  margin-right: 28px;
}
.login-btn {
  background-color: #6db4fb;
  border: none;
}
</style>
